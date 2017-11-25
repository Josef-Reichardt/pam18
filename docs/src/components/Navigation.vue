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
    background-color: fade(@lightgray, 50%);
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
                padding: 10px 16px;
                display: block;
                &:hover {
                    border: none;
                    >span {
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

</style>

<template>

<nav>
    <ul>
        <li><a href="#pam18" :class="{ active: currentHash=='pam18' }"><span>#pam18</span></a></li>
        <li><a href="#location" :class="{ active: currentHash=='location' }"><span>Wann &amp; Wo?</span></a></li>
        <li><a href="#speaker" :class="{ active: currentHash=='speaker' }"><span>Wer?</span></a></li>
    </ul>
</nav>

</template>

<script>

export default {
    name: 'Navigation',
    data() {
        return {
            currentHash: 'test'
        };
    },
    methods: {
        handleHashChange() {
            this.currentHash = window.location.hash.replace(/^#/, '');
        }
    },
    created() {
        window.addEventListener('hashchange', this.handleHashChange);
        this.handleHashChange();
    },
    destroyed() {
        window.removeEventListener('hashchange', this.handleHashChange);
    }
};

</script>
