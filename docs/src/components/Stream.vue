<style lang="less">
@import "../assets/variables.less";
[id]#stream {
    border-left-color: @lila;
    padding: 40px 0;
    h3 {
        margin: 0 20px 10px;
    }
    .youtube_wrapper {
        margin: 0 auto;
        max-width: 100%;
        width: 600px;
        height: 337px;
        background: @black;
    }
    .hidden {
        background: fade(@darkgray, 70%);
        width: 100%;
        position: relative;
        cursor: pointer;
        &.youtube_wrapper::before {
            content: '\F167';
            font: normal normal normal 42px/1 FontAwesome;
            text-align: center;
            color: @lightgray;
            position: absolute;
            bottom: 51%;
            left: 0;
            right: 0;
        }
        &::after {
            content: 'anzeigen';
            text-align: center;
            color: @lightgray;
            position: absolute;
            top: 51%;
            left: 0;
            right: 0;
        }
        * {
            visibility: hidden;
        }
    }
}

@media (min-width: 1200px) {
    [id]#stream {
        padding: 40px 20px;
        h3 {
          margin-left: 0;
        }
    }
}
</style>

<template>
<section id="stream">
    <h3><i class="fa fa-video-camera"></i> Aufzeichnung</h3>
    <div class="stream_row" ref="streamRow">
        <div class="youtube_wrapper hidden" @click="youTubeClick" ref="youtubeWrapper">
        </div>
    </div>
</section>
</template>

<script>
export default {
    name: 'Stream',
    methods: {
        youTubeClick() {
            if (this.$refs.youtubeWrapper.className.match(/hidden/)) {
                this.initYouTube();
                this.$refs.youtubeWrapper.className = this.$refs.youtubeWrapper.className.replace(/hidden/, '');
            }
        },
        initYouTube() {
            const html = '<iframe width="100%" height="100%" src="https://www.youtube-nocookie.com/embed/bLg7QyU2SzE?rel=0&autoplay=1" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>';
            this.$refs.youtubeWrapper.innerHTML = html;
        }
//         ,
//         handleResize() {
//             const height = Math.min(300, this.$refs.youtubeWrapper.clientWidth / 16 * 9) + 'px';
//             this.$refs.youtubeWrapper.style.height = height;
// 533
//             if (this.$refs.streamRow.clientWidth > (1200 - 40)) {
//                 this.$refs.streamRow.style.height = height;
//             }
//             else {
//                 this.$refs.streamRow.style.height = 'auto';
//             }
//         }
    },
    mounted: function() {
        // window.addEventListener('resize', this.handleResize)
        // this.handleResize();
    },
    beforeDestroy: function() {
        // window.removeEventListener('resize', this.handleResize)
    }
};
</script>
