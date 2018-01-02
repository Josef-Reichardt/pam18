<style lang="less">
@import "../assets/variables.less";

&.facebook,
&.twitter {
    border: none;
    .fa-stack-2x {
        text-shadow: 0 0 2px fade(@darkgray, 70%);
      }
    .fa-stack-1x {
        text-shadow: 0 0 1px fade(@darkgray, 70%);
    }
}
&.facebook:hover,
&.twitter:hover {
    border: none;
    .fa-stack-1x {
        text-shadow: 0 0 3px fade(@darkgray, 70%);
    }
}

&.twitter {
    color: #4AB3F4;
}

&.facebook {
    color: #4267B2;
}
</style>

<template>
<a :href="href" :class="wrapperClass" :title="title">
  <i class="fa fa-circle fa-stack-2x"></i>
  <i :class="iconClass"></i>
</a>
</template>

<script>
export default {
    name: 'IconLink',
    props: ['icon', 'href', 'title'],
    computed: {
        wrapperClass() {
            return 'fa-stack ' + this.icon;
        },
        iconClass() {
            return 'fa fa-stack-1x fa-inverse fa-' + this.icon;
        }
    }
};
</script>
