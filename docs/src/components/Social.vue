<style scoped lang="less">
@import "../assets/variables.less";
[id]#social {
    border-left-color: @darkgray;
    h3 {
        margin-bottom: 10px;
    }
    .twitter_wrapper {
        width: 100%;
        background: @white;
    }
    .facebook_wrapper {
        margin-top: 30px;
        width: 100%;
        text-align: center;
    }
}

@media (min-width: 768px) {
    [id]#social {
        .social_row {
            position: relative;
            .twitter_wrapper {
                margin-right: 10px;
                width: ~"calc( 100% - 370px )";
            }
            .facebook_wrapper {
                width: 350px;
                position: absolute;
                top: 0;
                right: 0;
                margin: 0;
            }
        }
    }
}
a.twitter-timeline {
   color: #333;
 }
a.twitter-timeline:hover,
a.twitter-timeline:focus {
  background-color: #333;
}
</style>

<template>
<section id="social">
  <h3>Social</h3>
  <div class="social_row">
    <div class="twitter_wrapper">
      <a class="twitter-timeline" href="https://twitter.com/hashtag/pam18" data-widget-id="935979645442371584"
       data-chrome="noborders noheader nofooter" data-width="100%" data-height="495"
       >#pam18-Tweets</a>
    </div>
    <div class="facebook_wrapper">
      <div class="fb-page" data-href="https://www.facebook.com/PiratenparteiBayern" data-tabs="timeline" data-width="350" data-height="500" data-small-header="true" data-adapt-container-width="true" data-hide-cover="true" data-show-facepile="false">
        <blockquote cite="https://www.facebook.com/PiratenparteiBayern" class="fb-xfbml-parse-ignore"><a href="https://www.facebook.com/PiratenparteiBayern">Piratenpartei Bayern</a></blockquote>
      </div>
    </div>
  </div>
</section>
</template>

<script>
export default {
  name: 'Social',
  mounted() {
    // Twitter
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

    // Facebook
    (function(d, s, id) {
      var js, fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) return;
      js = d.createElement(s);
      js.id = id;
      js.src = 'https://connect.facebook.net/de_DE/sdk.js#xfbml=1&version=v2.11';
      fjs.parentNode.insertBefore(js, fjs);
    }(document, 'script', 'facebook-jssdk'));
  }
};
</script>
