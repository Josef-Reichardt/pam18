<style scoped lang="less">

@import "../assets/variables.less";
nav {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    border-left: 15px solid @orange;
    padding: 0;
    z-index: 1;
    background-color: fade(@lightgray, 70%);
    ul {
        padding: 0;
        margin: 0;
        list-style: none;
        display: table-row;
        li {
            padding: 0;
            margin: 0;
            display: table-cell;
            a {
                padding: 10px 5px 10px 10px;
                display: block;
                &:hover {
                    border: none;
                    > span {
                        border-bottom: 2px solid @orange;
                    }
                }
                &.active,
                &:active {
                    color: @lila;
                }
            }
        }
    }
}

@media (min-width: 768px) {
nav ul li a {
  padding: 10px 16px;
}
}

</style>

<template>

<nav>
    <ul>
        <li><a data-scroll href="#pam18" :class="{ active: currentHash=='pam18' }"><span>#pam18</span></a></li>
        <li><a data-scroll href="#location" :class="{ active: currentHash=='location' }"><span>Wann &amp; Wo?</span></a></li>
        <li><a data-scroll href="#speaker" :class="{ active: currentHash=='speaker' }"><span>Redner?</span></a></li>
    </ul>
</nav>

</template>

<script>

window._ = require('lodash');
window.SmoothScroll = require('smooth-scroll');

export default {
    name: 'Navigation',
    data() {
        return {
            currentHash: ''
        };
    },
    methods: {
        handleScroll: _.debounce(function() {
            const allSections = Array.slice(document.querySelectorAll('section[id]')).sort(function(a, b) {
                return a.offsetTop - b.offsetTop;
            });
            let section = allSections[0];
            for (let i = 0; i < allSections.length; i++) {
                if (allSections[i].offsetTop + allSections[i].style.height <= window.scrollY + (window.innerHeight * 0.3)) {
                    section = allSections[i];
                }
            }
            this.currentHash = (section.id == 'wallpaper' ? 'pam18' : section.id);
            history.pushState(null, null, document.location.pathname + '#' + this.currentHash);
        }, 200),
        handleHashChange(event) {
            this.currentHash = window.location.hash.replace(/^#/, '');
        }
    },
    created() {
        window.addEventListener('scroll', this.handleScroll);
        window.addEventListener('hashchange', this.handleHashChange);

        var scroll = new SmoothScroll('a[data-scroll][href*="#"]');
    },
    destroyed() {
        window.removeEventListener('scroll', this.handleScroll);
        window.removeEventListener('hashchange', this.handleHashChange);
    }
};

</script>
