<template>
  <div class="map">
    <baidu-map
      :center="center"
      :zoom="zoom"
      @ready="handler"
      class="bm-view"
      :mapStyle="mapStyle"
    >
      <bm-scale anchor="BMAP_ANCHOR_TOP_RIGHT"></bm-scale>
      <bm-navigation anchor="BMAP_ANCHOR_TOP_RIGHT"></bm-navigation>
      <bm-overview-map
        anchor="BMAP_ANCHOR_BOTTOM_RIGHT"
        :isOpen="true"
      ></bm-overview-map>
    </baidu-map>
  </div>
</template>
<script>
export default {
  data() {
    return {
      center: { lng: 0, lat: 0 },
      zoom: 3,
      mapType: "BMAP_SATELLITE_MAP",
      mapStyle: {
        styleJson: [
          {
            featureType: "all",
            elementType: "geometry",
            stylers: {
              hue: "#007fff",
              saturation: 89
            }
          },
          {
            featureType: "water",
            elementType: "all",
            stylers: {
              color: "#ffffff"
            }
          }
        ]
      }
    };
  },
  mounted() {},
  methods: {
    handler({ BMap, map }) {
      console.log(BMap, map);
      this.center = "上海";
      // this.center.lng = 116.404
      // this.center.lat = 39.915
      this.zoom = 18;
    }
  }
};
</script>
<style lang="less" scoped>
.bm-view {
  width: 100%;
  // height: calc(100%-90px);
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
