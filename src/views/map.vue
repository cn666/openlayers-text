<script lang="ts" setup>
import {nextTick, onMounted, onBeforeUnmount , ref} from 'vue';
import 'ol/ol.css'; // 引入样式
import Map from 'ol/Map';
import View from 'ol/View';
import TileLayer from 'ol/layer/Tile';
import XYZ from 'ol/source/XYZ';
import OSM from 'ol/source/OSM';
const map = ref(null);
function initMap() {
  map.value = new Map({
    target: 'map',
    layers: [
      new TileLayer({
        source: new OSM(),
      }),
      new TileLayer({
        visible: true,
        source: new XYZ({
          visible: true,
          url: 'http://webrd01.is.autonavi.com/appmaptile?x={x}&y={y}&z={z}&lang=zh_cn&size=2&scale=1&style=8',
        })
      })
    ],
    view: new View({
      // projection: 'EPSG:3857',
      projection: "EPSG:4326",
      // center: [12964000, 4880000], // 在Web Mercator投影中指定的坐标
      center: [116.403218, 39.92372],
      constrainResolution: true,  // 设置缩放级别为整数
      smoothResolutionConstraint: false,  // 关闭无级缩放地图
      zoom: 12,
    }),
  });
  // https://tile.openstreetmap.org/{z}/{x}/{y}.png



}
// onMounted(()=>{
//   nextTick(() => {
//     initMap();
//
//   });
// })
onMounted(() => {
  initMap();
});


</script>

<template>
  <div id="map">地图</div>
</template>

<style scoped>
#map {
  width:100%;
  height: 100%;
}
</style>
