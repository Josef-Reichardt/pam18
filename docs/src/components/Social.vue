<style lang="less">
@import "../assets/variables.less";
[id]#social {
    border-left-color: @darkgray;
    padding: 40px 0;
    h3 {
        margin-bottom: 10px;
    }
    .youtube_wrapper {
        margin-top: 30px;
        width: 100%;
        background: @black;
    }
    .twitter_wrapper {
        width: 100%;
        background: @white;
    }
    .facebook_wrapper {
        margin-top: 30px;
        width: 100%;
        text-align: center;
        * {
            max-width: 100%;
            height: 100% !important;
        }
    }
    .hidden {
        background: fade(@darkgray, 70%);
        height: 500px;
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
        &.twitter_wrapper::before {
            content: '\F099';
            font: normal normal normal 42px/1 FontAwesome;
            text-align: center;
            color: @lightgray;
            position: absolute;
            bottom: 51%;
            left: 0;
            right: 0;
        }
        &.facebook_wrapper::before {
            content: '\F09A';
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
    [id]#social {
        padding: 40px 20px;
        .social_row {
            position: relative;
            .youtube_wrapper {
                width: ~"calc( 50% - 20px )";
                position: absolute;
                left: 0;
                top: 0;
                margin: 0;
            }
            .twitter_wrapper {
                width: ~"calc( 25% - 20px )";
                position: absolute;
                left: ~"calc( 50% + 10px )";
                top: 0;
                // margin-right: 10px;
                // width: ~"calc( 100% - 370px )";
            }
            .facebook_wrapper {
                width: ~"calc( 25% - 20px )";
                position: absolute;
                right: 0;
                top: 0;
                // width: 350px;
                // position: absolute;
                // top: 0;
                // right: 0;
                margin: 0;
            }
        }
    }
}
a.twitter-timeline {
    color: #333;
}
a.twitter-timeline:focus,
a.twitter-timeline:hover {
    background-color: #333;
}
</style>

<template>
<section id="social">
    <h3>Social</h3>
    <div class="social_row" ref="socialRow">
        <div class="youtube_wrapper hidden" @click="youTubeClick" ref="youtubeWrapper">
        </div>
        <div class="twitter_wrapper hidden" @click="twitterClick" ref="twitterWrapper">
            <a class="twitter-timeline" href="https://twitter.com/hashtag/pam18" data-widget-id="935979645442371584" data-chrome="noborders noheader nofooter" data-width="100%" data-height="100%">#pam18-Tweets</a>
        </div>
        <div class="facebook_wrapper hidden" @click="facebookClick" ref="facebookWrapper">
            <div class="fb-page" data-href="https://www.facebook.com/PiratenparteiBayern" data-tabs="events,timeline" data-width="500" data-height="500" data-small-header="true" data-adapt-container-width="true" data-hide-cover="true" data-show-facepile="false">
                <blockquote cite="https://www.facebook.com/PiratenparteiBayern" class="fb-xfbml-parse-ignore"><a href="https://www.facebook.com/PiratenparteiBayern">Piratenpartei Bayern</a></blockquote>
            </div>
            <!--<div class="fb-post" data-href="https://www.facebook.com/PiratenparteiBayern/posts/1650706761655726" data-width="100%" data-show-text="true">
                <blockquote cite="https://www.facebook.com/PiratenparteiBayern/posts/1650706761655726" class="fb-xfbml-parse-ignore">Posted by <a href="https://www.facebook.com/PiratenparteiBayern/">Piratenpartei Bayern</a> on&nbsp;<a href="https://www.facebook.com/PiratenparteiBayern/posts/1650706761655726">Donnerstag, 4. Januar 2018</a></blockquote>
            </div>-->
        </div>
    </div>
</section>
</template>

<script>
export default {
    name: 'Social',
    methods: {
        youTubeClick() {
            if (this.$refs.youtubeWrapper.className.match(/hidden/)) {
                this.initYouTube();
                this.$refs.youtubeWrapper.className = this.$refs.youtubeWrapper.className.replace(/hidden/, '');
            }
        },
        twitterClick() {
            if (this.$refs.twitterWrapper.className.match(/hidden/)) {
                this.initTwitter();
                this.$refs.twitterWrapper.className = this.$refs.twitterWrapper.className.replace(/hidden/, '');
            }
        },
        facebookClick() {
            if (this.$refs.facebookWrapper.className.match(/hidden/)) {
                this.initFacebook();
                this.$refs.facebookWrapper.className = this.$refs.facebookWrapper.className.replace(/hidden/, '');
            }
        },
        initYouTube() {
            const html = '<iframe width="100%" height="100%" src="https://www.youtube-nocookie.com/embed/W-vnmWQRVI4?rel=0&autoplay=1" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>';
            this.$refs.youtubeWrapper.innerHTML = html;
        },
        initTwitter() {
            (function(d, s, id) {
                var js, fjs = d.getElementsByTagName(s)[0],
                    p = /^http:/.test(d.location) ? 'http' : 'https';
                if (!d.getElementById(id)) {
                    js = d.createElement(s);
                    js.id = id;
                    js.src = p + "://platform.twitter.com/widgets.js";
                    fjs.parentNode.insertBefore(js, fjs);
                }
            }(document, "script", "twitter-wjs"));
        },
        initFacebook() {
            (function(d, s, id) {
                var js, fjs = d.getElementsByTagName(s)[0];
                if (d.getElementById(id)) return;
                js = d.createElement(s);
                js.id = id;
                js.src = 'https://connect.facebook.net/de_DE/sdk.js#xfbml=1&version=v2.11';
                fjs.parentNode.insertBefore(js, fjs);
            }(document, 'script', 'facebook-jssdk'));
        },
        handleResize() {
            const height = (this.$refs.youtubeWrapper.clientWidth / 848 * 481) + 'px';
            this.$refs.youtubeWrapper.style.height =
                this.$refs.twitterWrapper.style.height =
                this.$refs.facebookWrapper.style.height = height;

            if (this.$refs.socialRow.clientWidth > (1200 - 40)) {
                this.$refs.socialRow.style.height = height;
            }
            else {
                this.$refs.socialRow.style.height = 'auto';
            }
        }
    },
    mounted: function() {
        window.addEventListener('resize', this.handleResize)
        this.handleResize();
    },
    beforeDestroy: function() {
        window.removeEventListener('resize', this.handleResize)
    }
};
</script>
