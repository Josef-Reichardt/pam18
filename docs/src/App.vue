<style lang="less">
@import "assets/variables.less";

/* fonts: */

@font-face {
    font-family: "DejaWeb";
    src: url("assets/fonts/dejaweb/DejaWeb.eot");
    src: url("assets/fonts/dejaweb/DejaWeb.eot?#iefix") format("embedded-opentype"), url("assets/fonts/dejaweb/DejaWeb.woff2") format("woff2"), url("assets/fonts/dejaweb/DejaWeb.woff") format("woff"), url("assets/fonts/dejaweb/DejaWeb.ttf") format("truetype"), url("assets/fonts/dejaweb/DejaWeb.svg#DejaWeb") format("svg");
}

@font-face {
    font-family: "Roboto";
    src: url("assets/fonts/roboto/Roboto.eot");
    src: url("assets/fonts/roboto/Roboto.eot?#iefix") format("embedded-opentype"), url("assets/fonts/roboto/Roboto.woff2") format("woff2"), url("assets/fonts/roboto/Roboto.woff") format("woff"), url("assets/fonts/roboto/Roboto.ttf") format("truetype"), url("assets/fonts/roboto/Roboto.svg#Roboto Regular V2") format("svg");
}

/* basic styles: */

body {
    padding: 0;
    margin: 0;
    font-family: DejaWeb, sans-serif;
    text-rendering: geometricPrecision;
    color: @black;
    background: @white;
    > #app > footer > section,
    > #app > main > section {
        min-height: 300px;
        border-left: 15px solid @darkgray;
        padding: 40px 20px;
        background: @white;
        &:nth-child(2n+0) {
            background: @lightgray;
        }
    }
}

header {
    font-family: Roboto, sans-serif;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-family: Roboto, sans-serif;
    color: @lila;
    padding: 0;
    margin: 0;
}

h1 {
    font-size: 34px;
}

h2 {
    font-size: 30px;
}

h3 {
    font-size: 26px;
}

h4 {
    font-size: 22px;
}

h5 {
    font-size: 18px;
}

h6 {
    font-size: 16px;
}

p {
    padding: 0;
    margin: 0;
}

a {
    color: @darkgray;
    text-decoration: none;
    &:hover {
        border-bottom: 2px solid @orange;
    }

    &.facebook,
    &.twitter {
        font-size: 0.8em;
        color: @lightgray;
        padding: 4px;
        border-radius: 20px;
        position: relative;
        overflow: visible;
        content: ' ';
        width: 16px;
        height: 16px;
        display: inline-block;
        vertical-align: text-bottom;
        background: none no-repeat center center transparent;
        span {
            display: none;
            position: absolute;
            top: -80%;
            left: ~"calc( -50% - 10px )";
            background: @darkgray;
            padding: 2px 4px;
            border-radius: 2px;
            box-shadow: 0 0 2px @darkgray;
            white-space: nowrap;
            z-index: 999;
        }
        &:hover {
            border: none;
            span {
                display: block;
            }
        }
    }
    &.twitter {
        background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAA+ElEQVQ4jcXTzytFQRjG8c85C0ny6yh2NxtlYcGClFK47G6RrG1t1N1Y+FEIXQtlY2mp+C+UnYW/yeLMqeN4010o35qaeZ9n3nnfmYZ/Jq8vVpAFpgw7uEhjHkM4xVZlGsArToIEZ1ir+Y5wiTecV6YF7CXjHYoUn8NBkHQaT2hXgRYO07xIldzgGbNBgnV064FlvKfe6kymspt0a1WCqRTMA3PEteDCHzDTx+Yct5HQTkmabTTZxWokZH1UUShf6RvjGE3iJj6xGGyewCNGmsISPvCCbQw29Bwd3KeDQnLso4cr5YscK2+7h41f2vpBhjEMi//G3/IFbSgcAvdh4fkAAAAASUVORK5CYII=");
        background-color: #4AB3F4;
    }

    &.facebook {
        background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAXklEQVQ4je3PoQ2AUAxF0eOQGBZgE9ZBQ7CAZwzGQPzRMFUEUwRBcJPm1bybli9TYcUcU7KCHi1qDDiygjlyQpMtw3LJFAVj7F1IUi/cCfbsFcsl0/wCtiiXp4J3OAE/+RIs6cJYHgAAAABJRU5ErkJggg==");
        background-color: #4267B2;
    }
}
</style>

<template>
<div id="app">
  <header id="pam18">
    <navigation/>
    <wallpaper/>
  </header>
  <main>
    <intro/>
    <location/>
    <speaker/>
    <social/>
  </main>
  <footer>
    <contact/>
  </footer>
</div>
</template>

<script>
import Navigation from '@/components/Navigation';
import Wallpaper from '@/components/Wallpaper';
import Intro from '@/components/Intro';
import Location from '@/components/Location';
import Speaker from '@/components/Speaker';
import Social from '@/components/Social';
import Contact from '@/components/Contact';

export default {
  name: 'app',
  components: {
    Navigation,
    Wallpaper,
    Intro,
    Location,
    Speaker,
    Social,
    Contact
  },
  mounted() {
    if (localStorage.getItem('showBody') !== 'true') {
      document.body.style.opacity = 0;
      if (prompt('Dies ist eine Vorschau! Zur Anzeige bitte den Schlüssel eingeben... ;)') === '#pam18') {
        document.body.style.opacity = 1;
        localStorage.setItem('showBody', 'true');
      }
    }
  }
};
</script>
