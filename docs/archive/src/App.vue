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
    font-size: 16px;
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
    border-bottom: 2px solid transparent;
    &:hover {
        border-bottom-color: @orange;

    }
    &.no-border,
    &.no-border:hover {
        border: none;
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
        <stream/>
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
import Stream from '@/components/Stream';
import Social from '@/components/Social';
import Contact from '@/components/Contact';

require('font-awesome/css/font-awesome.css');

export default {
    name: 'app',
    components: {
        Navigation,
        Wallpaper,
        Intro,
        Location,
        Speaker,
        Stream,
        Social,
        Contact
    }
};
</script>
