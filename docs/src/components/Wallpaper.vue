<style lang="less">

@import "../assets/variables";
#wallpaper {
    >img {
        width: 100%;
        position: fixed;
        left: 0;
        z-index: -1;
    }
    >hgroup {
        position: relative;
        height: 200px;
        z-index: 0;
        > h1 {
            text-transform: uppercase;
            font-size: 16px;
            font-weight: bold;
            color: @darkgray;
            >span {
                position: absolute;
                padding: 2px 10px;
                background: @white;
                border-color: @darkgray;
                border-style: solid;
            }
            > .h1-part1 {
                top: 79px;
                left: 40px;
                transform: rotate(-2deg);
                z-index: 1;
                border-width: 2px 5px 3px 1px;
            }
            > .h1-part2 {
                font-size: 20px;
                top: 108px;
                left: 30px;
                transform: rotate(1deg);
                z-index: 0;
                border-width: 2px 1px 4px 7px;
                color: @orange;
            }
            > .h1-part3, > .h1-part4 {
                top: 170px;
                left: 0;
                padding-right: 20px;
                z-index: 1;
                color: @lila;
                background: fade(@lightgray, 50%);
                border: 0;
            }
            > .h1-part4 {
                left: auto;
                right: 0;
            }
        }
        > h2 {
            position: absolute;
            font-size: 20px;
            top: 50px;
            right: 20px;
            transform: rotate(10deg);
            text-shadow: 0 0 3px @lightgray;
            a {
                color: @lila;
            }
        }
    }
}

@media (min-width: 768px) {
    #wallpaper>hgroup {
        height: 400px;
        > h1 {
            font-size: 30px;
            > .h1-part1 {
                top: 127px;
                left: 60px;
                border-width: 2px 6px 5px 1px;
            }
            > .h1-part2 {
                font-size: 34px;
                top: 175px;
                left: 50px;
                border-width: 2px 1px 5px 8px;
            }
            > .h1-part3, > .h1-part4 {
                top: 310px;
            }
            > .h1-part3 {
              padding-left: 50px;
            }
            > .h1-part4 {
              padding-right: 50px;
            }
        }
        > h2 {
            font-size: 34px;
            top: 70px;
            right: 50px;
        }
    }
}

@media (min-width: 1200px) {
    #wallpaper>hgroup {
        height: 500px;
        > h1 {
            font-size: 42px;
            > .h1-part1 {
                top: 180px;
                left: 110px;
                border-width: 3px 8px 6px 2px;
            }
            > .h1-part2 {
                font-size: 60px;
                top: 240px;
                left: 90px;
                border-width: 3px 2px 6px 10px;
            }
            > .h1-part3, > .h1-part4 {
                top: 400px;
            }
            > .h1-part3 {
              padding-left: 90px;
            }
            > .h1-part4 {
              padding-right: 90px;
            }
        }
        > h2 {
            font-size: 60px;
            top: 100px;
            right: 90px;
        }
    }
}

</style>

<template>

<section id="wallpaper">
    <img src="../assets/wallpaper.jpg" alt="wallpaper beer" :style="imgStyle">
    <hgroup>
        <h1>
          <span class="h1-part1">Piratiger</span>
          <span class="h1-part2">Aschermittwoch</span>
          <span class="h1-part3">Straubing</span>
          <span class="h1-part4">14.02.2018</span>
        </h1>
        <h2><a href="#social">#pam18</a></h2>
    </hgroup>
</section>

</template>

<script>

export default {
    name: 'Wallpaper',
    data() {
        return {
            imgStyle: {
                top: '0px'
            }
        }
    },
    methods: {
        handleScroll() {
            this.imgStyle.top = (-parseInt(window.scrollY / 2)) + 'px';
        }
    },
    created() {
        window.addEventListener('scroll', this.handleScroll);
    },
    destroyed() {
        window.removeEventListener('scroll', this.handleScroll);
    }
};

</script>
