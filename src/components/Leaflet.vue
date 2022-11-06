<template>
  <div id="map"></div>
  <button type="button" @click="getData()">Pass data</button>
  <TestPassData @getData="getData()" />
</template>

<script>
import * as L from "leaflet";
import TestPassData from "./TestPassData.vue";
export default {
  name: "Leaflet",
  emits: ["getData"],
  data() {
    return {
      lastLat: Object,
    };
  },
  mounted() {
    this.initmap();
  },
  methods: {
    initmap() {
      let map = L.map("map").setView([30.183601, -85.647209], 18);
      L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 19,
        attribution:
          '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
      }).addTo(map);
      this.lastLat = map.getCenter();
    },
    checkMap() {
      this.lastLat = this.map.getCenter();
      console.log("checkMap", lastLat);
    },
    getData() {
      this.$emit("getData");
    },
  },
  watch: {
    lastLat(val, oldVal) {
      console.log(`new: ${val}, old: ${oldVal}`);
    },
  },
  components: { TestPassData },
};
</script>
<style>
#map {
  height: 500px;
}
</style>
