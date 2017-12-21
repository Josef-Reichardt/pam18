<style lang="less">
@import "../assets/variables";
#wallpaper {
    > img {
        width: 100%;
        position: fixed;
        left: 0;
        z-index: -1;
    }
    > hgroup {
        position: relative;
        padding: 50px 20px 20px;
        z-index: 0;
        > h1 {
            width: 75%;
            img {
                width: 100%;
            }
        }
        h2 {
            font-size: 20px;
            text-shadow: 0 0 3px @lightgray;
        }
        > h2.location {
            float: right;
        }
        > h2.pam18 {
            position: absolute;
            top: 50px;
            right: 20px;
            transform: rotate(10deg);
            a {
                color: @lila;
            }
        }
    }
}

@media (min-width: 768px) {
    #wallpaper > hgroup {
        padding: 100px 50px 50px;
        > h1 {
            margin-bottom: 50px;
        }
        > h2 {
            font-size: 34px;
        }
        > h2.pam18 {
            top: 100px;
            right: 50px;
        }
    }
}

@media (min-width: 1200px) {
    #wallpaper > hgroup {
        padding: 100px 90px 90px;
        > h1 {
            // margin-bottom: 50px;
            width: 60%;
        }
        > h2 {
            font-size: 60px;
        }
        > h2.pam18 {
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
    <h1 :style="headerStyle"><img src="../assets/Piratiger-Aschermittwoch.svg" alt="Piratiger Aschermittwoch"/></h1>
    <h2 class="location" :style="locationStyle">Straubing</h2>
    <h2 class="date" :style="dateStyle">14.02.2018</h2>
    <h2 class="pam18" :style="pam18Style"><a href="#social">#pam18</a></h2>
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
      },
      headerStyle: {
        textIndent: '0px'
      },
      locationStyle: {
        textIndent: '0px'
      },
      dateStyle: {
        textIndent: '0px'
      },
      pam18Style: {
        textIndent: '0px'
      }
    }
  },
  methods: {
    handleScroll() {
      this.imgStyle.top = (-parseInt(window.scrollY / 2)) + 'px';
      this.headerStyle.marginLeft = (-window.scrollY) + 'px';
      this.locationStyle.marginRight = (-Math.max(0, window.scrollY - (document.getElementById('wallpaper').clientHeight / 2))) + 'px';
      this.dateStyle.marginLeft = (-Math.max(0, window.scrollY - (document.getElementById('wallpaper').clientHeight / 2))) + 'px';
      this.pam18Style.marginRight = (-window.scrollY) + 'px';
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
