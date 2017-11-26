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
            color: @lightgray;
            text-shadow: 1px 1px 0 @orange;
            >span {
                position: absolute;
                background-color: @darkgray;
                padding: 2px 15px;
                box-shadow: -2px 2px 0 @lila;
                border: 1px solid @darkgray;
                border-radius: 1px;
            }
            > .h1-part1 {
                top: 80px;
                left: 40px;
                transform: rotate(-2deg);
                z-index: 1;
            }
            > .h1-part2 {
                font-size: 20px;
                top: 108px;
                left: 30px;
                transform: rotate(1deg);
                z-index: 0;
            }
            > .h1-part3 {
                top: 142px;
                left: 160px;
                transform: rotate(-2deg);
                z-index: 1;
                background-color: @lila;
                color: @lightgray;
                border: 1px solid @orange;
                box-shadow: 2px 2px 0 @darkgray;
                text-shadow: 1px 1px 0 @darkgray;
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
                top: 170px;
                left: 60px;
            }
            > .h1-part2 {
                font-size: 34px;
                top: 215px;
                left: 50px;
            }
            > .h1-part3 {
                top: 265px;
                left: 250px;
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
            }
            > .h1-part2 {
                font-size: 60px;
                top: 240px;
                left: 90px;
            }
            > .h1-part3 {
                top: 320px;
                left: 470px;
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
          <span class="h1-part3">2018</span>
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
