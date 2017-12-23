<style scoped lang="less">
@import "../assets/variables.less";
[id]#location {
    border-left-color: @lila;
    padding: 40px 0;
    overflow: hidden;
    h3 {
        padding: 0 20px 10px;
    }
    p.time {
        padding: 0 20px 10px;
    }
    #map {
        width: 100%;
        height: 200px;
        cursor: pointer;
        display: block;
        border: none;
    }
    #map-marker {
        width: 20px;
        height: 20px;
        border-radius: 10px;
        border: 1px solid fade(@white, 50%);
        box-shadow: 0 0 0 2px @orange;
    }
    p {
        padding: 10px 20px 0;
    }
    b {
        font-weight: normal;
        color: @orange;
    }
}

@media (min-width: 768px) {
    [id]#location {
        min-height: 300px;
        padding-left: ~"calc(50% + 50px)";
        position: relative;
        #map {
            width: 50%;
            height: 300px;
            position: absolute;
            left: 20px;
            top: 40px;
            border: 10px solid fade(@darkgray, 10%);
        }
    }
}

@media (min-width: 1200px) {
    [id]#location {
        padding-left: 40%;
        #map {
            width: 30%;
        }
    }
}
</style>

<template>
<section id="location">
  <h3 :style="textStyle">Wann &amp; Wo?</h3>
  <p class="time" :style="textStyle">
    <time datetime="2018-02-14T14:00:00">14. Februar 2018 14:00 Uhr</time>
  </p>
  <a id="map" class="map" href="https://www.openstreetmap.org/way/154535030" :style="mapStyle"></a>
  <img id="map-marker" src="../assets/icon.svg">
  <p :style="textStyle"><b>Magnobonus-Markmiller-Saal</b></p>
  <p :style="textStyle">Äußere Passauer Straße 60
    <br>94315 Straubing</p>
</section>
</template>

<script>
import Map from 'ol/map';
import TileLayer from 'ol/layer/tile';
import OSM from 'ol/source/osm';
import View from 'ol/view';
import proj from 'ol/proj';
import Overlay from 'ol/overlay';
import interaction from 'ol/interaction';
import control from 'ol/control';

export default {
  name: 'Location',
  data() {
    return {
      mapStyle: {
        marginLeft: '0px'
      },
      textStyle: {
        marginLeft: '0px'
      }
    }
  },
  methods: {
    handleScroll() {
      const locationHeight = document.getElementById('location').clientHeight;
      const offset = document.getElementById('wallpaper').clientHeight +
        document.getElementById('intro').clientHeight +
        (document.getElementById('location').clientHeight * 0.75);
      const scrollBottom = window.scrollY + window.innerHeight;
      const marginLeft = -Math.max(0, offset - scrollBottom);
      this.mapStyle.marginLeft = parseInt(marginLeft) + 'px';
      this.mapStyle.opacity = 1 - Math.min(1, Math.max(0, (offset - scrollBottom) / window.innerHeight * 5));
      this.textStyle.opacity = this.mapStyle.opacity;
    }
  },
  created() {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  mounted() {
    this.$nextTick(function() {
      const coordinates = proj.fromLonLat([12.584559, 48.873665]);
      let map = new Map({
        target: 'map',
        layers: [
          new TileLayer({
            source: new OSM()
          })
        ],
        view: new View({
          center: coordinates,
          zoom: 13
        }),
        interactions: interaction.defaults({
          mouseWheelZoom: false,
          dragPan: false
        }),
        loadTilesWhileAnimating: true,
        controls: control.defaults({
          attribution: false,
          rotate: false,
          zoom: false
        })
      });
      map.addOverlay(new Overlay({
        element: document.getElementById('map-marker'),
        position: coordinates,
        offset: [-10, -10]
      }));
    })
  }
};
</script>
