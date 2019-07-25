<template>
  <header class="o-header">
    <h1>Hello world</h1>
    <div class="toggle-btn">
      <span class="one"></span><span class="two"></span>
    </div>
    <div class="o-header__menu">
      <div class="o-header__data">
        <ul>
          <li><a href="#">one</a></li>
          <li><a href="#">two</a></li>
          <li><a href="#">three</a></li>
          <li><a href="#">four</a></li>
          <li><a href="#">five</a></li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        msg: String
    },
    data() {
        return {

        }
    },
    methods: {
    
    },
    mounted() {

        // tweenmax menu load
        var t1 = this.t1;
        t1 = new TimelineMax({paused: true});

        t1.to('.one', 0.35, {
            y:6,
            rotation: 45,
            ease: Expo.easeInOut
        });

        t1.to('.two', 0.35, {
            y:-6,
            rotation: -45,
            ease: Expo.easeInOut,
            delay: -0.35
        });

        t1.to('.o-header__menu', 0.75, {
        
            top: "0%",
            ease: Expo.easeInOut,
            delay: -0.75
        });

        t1.staggerFrom('.o-header__menu ul li', 0.75, {x: -200, opacity: 0, ease:Expo.easeOut}, 0.3);

        t1.reverse();
        
        // tweenmax menu toggle
        $('.toggle-btn').on('click', () => {
            t1.reversed(!t1.reversed());
        })
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="scss">
    $teal: #67eaca;
    $lightpuple: #ccc1ff;
    $backgrundBlack: #222831;
    $activeNav: #dbe2ef;

    $LoraFont: 'Lora', serif;
    .o-header {
        background-blend-mode: multiply, color;
        background-image: url(../assets/background.jpg), linear-gradient(to bottom, rgba($teal, 0.75), rgba($lightpuple, 0.75));
        background-size: cover;
        background-position: center;
        width: 100%;
        height: 100vh;
        font-family: 'Literata', serif;
        &__menu {
            position: absolute;    
            z-index: 0;
            background-color: $backgrundBlack;
            width: 100%;
            height: 100vh;
            top: -100%;
        } 

        &__data {
            padding: 8em 0 0 2em;
            text-align: left;
        }

        ul {
            list-style-type: none;
            li {
                font-family: $LoraFont;
                &:first-child {
                    a {
                        color: $activeNav;
                        font-size: 24px;
                    }
                }
                &:not(:first-child) {
                    a{
                        color: #ffffff;
                        font-size: 42px;
                    }
                }

                a{
                    text-decoration: none;
                }
            }
        }

        h1 {
            position: absolute;
            top: 46%;
            left: 50%;
            transform: translate(-50%,-50%);
            color: #ffffff;
            font-size: 48px;
            font-weight: lighter;
        }

        .toggle-btn {
            position: fixed;
            margin: 1.4em;
            padding: 1em;
            width: 40px;
            height: 12px;
            right: 0;
            z-index: 1;
        }

        span{
            &.one,&.two {
                position: absolute;
                width: 40px;
                height: 2px;
                background: #ffffff;
            }
            &.two {
                margin-top: 12px;
            }
        }
    }
</style>
