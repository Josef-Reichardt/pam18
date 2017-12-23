<style scoped lang="less">
@import "../assets/variables.less";
[id]#speaker {
    border-left-color: @lightgray;
    overflow: hidden;

    ul {
        list-style: none;
        padding: 0;
        margin: 20px 0 0;

        li {
            padding: 30px 20px 0 160px;
            margin: 0 0 20px;
            position: relative;
            min-height: 100px;

            img {
                position: absolute;
                top: 0;
                left: 20px;
                width: 100px;
                height: 100px;
                border-radius: 100px;
                border: 3px solid @white;
                box-shadow: 0 0 0 5px @black;
            }
        }
    }
}
</style>

<template>
<section id="speaker">
  <h3>Redner?</h3>

  <ul>
    <li id="speaker-first-li" :style="textStyle1">
      <img src="../assets/speaker/Astrid_Semm_Icon.jpg" alt="Astrid Semm" :style="imgStyle1" />
      <strong>Astrid Semm</strong>
      <a href="https://twitter.com/mertl0rn" class="twitter"><span>@mertl0rn</span></a>
      <a href="https://www.facebook.com/Mertl0r" class="facebook"><span>Martina Michaela Wenta</span></a><br> Stellvertretende Politische Geschäftsführerin, Piratenpartei Deutschland
    </li>
    <li :style="textStyle2">
      <img src="../assets/speaker/Piratenlily_Icon.jpg" alt="Piratenlily" :style="imgStyle2" />
      <strong>Ute Elisabeth Gabelmann</strong>
      <a href="https://twitter.com/mertl0rn" class="twitter"><span>@mertl0rn</span></a>
      <a href="https://www.facebook.com/Mertl0r" class="facebook"><span>Martina Michaela Wenta</span></a><br> Ehemalige Politische Geschäftsführerin, Piratenpartei Deutschland
    </li>
    <li :style="textStyle3">
      <img src="../assets/speaker/Benjamin_Wildenauer_Icon.jpg" alt="Benjamin Wildenauer" :style="imgStyle3" />
      <strong>Benjamin Wildenauer</strong>
      <a href="https://twitter.com/mertl0rn" class="twitter"><span>@mertl0rn</span></a>
      <a href="https://www.facebook.com/Mertl0r" class="facebook"><span>Martina Michaela Wenta</span></a><br> Stellvertretender Politischer Geschäftsführer, Piratenpartei Bayern
    </li>
    <li :style="textStyle4">
      <img src="../assets/speaker/Benjamin_Wildenauer_Icon.jpg" alt="Benjamin Wildenauer" :style="imgStyle4" />
      <strong>Benjamin Wildenauer</strong>
      <a href="https://twitter.com/mertl0rn" class="twitter"><span>@mertl0rn</span></a>
      <a href="https://www.facebook.com/Mertl0r" class="facebook"><span>Martina Michaela Wenta</span></a><br> Stellvertretender Politischer Geschäftsführer, Piratenpartei Bayern
    </li>
    <li :style="textStyle5">
      <img src="../assets/speaker/Benjamin_Wildenauer_Icon.jpg" alt="Benjamin Wildenauer" :style="imgStyle5" />
      <strong>Benjamin Wildenauer</strong>
      <a href="https://twitter.com/mertl0rn" class="twitter"><span>@mertl0rn</span></a>
      <a href="https://www.facebook.com/Mertl0r" class="facebook"><span>Martina Michaela Wenta</span></a><br> Stellvertretender Politischer Geschäftsführer, Piratenpartei Bayern
    </li>
  </ul>
</section>
</template>

<script>
export default {
  name: 'Speaker',
  data() {
    return {
      textStyle1: {
        opacity: 1
      },
      imgStyle1: {
        marginLeft: '0px',
        transform: 'rotate(0deg)'
      },
      textStyle2: {
        opacity: 1
      },
      imgStyle2: {
        marginLeft: '0px'
      },
      textStyle3: {
        opacity: 1
      },
      imgStyle3: {
        marginLeft: '0px'
      },
      textStyle4: {
        opacity: 1
      },
      imgStyle4: {
        marginLeft: '0px'
      },
      textStyle5: {
        opacity: 1
      },
      imgStyle5: {
        marginLeft: '0px'
      }
    }
  },
  methods: {
    handleScroll() {
      const offset = document.getElementById('wallpaper').clientHeight +
        document.getElementById('intro').clientHeight +
        document.getElementById('location').clientHeight +
        (document.getElementById('speaker').clientHeight * 0.75);
      const scrollBottom = window.scrollY + window.innerHeight;
      const liHeight = document.getElementById('speaker-first-li').clientHeight;
      for (let i = 0; i < 5; i++) {
        const val = Math.min(1, Math.max(0, (offset - ((3 - i) * liHeight) - scrollBottom) / window.innerHeight * 5));
        this['textStyle' + (i + 1)].opacity = 1 - val;
        this['imgStyle' + (i + 1)].marginLeft = '-' + (val * 100) + 'px';
        this['imgStyle' + (i + 1)].transform = 'rotate(-' + (val * 100) + 'deg)';
      }
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
