<template>
  <div id="center">
    <baidu-map class="bm-view" :center="center" :zoom="zoom" :scroll-wheel-zoom="true" @ready="handler">
    </baidu-map>
  </div>
</template>

<script>

export default {
  data () {
    return {
      center: { lng: 0, lat: 0 },
      zoom: 9,
      stationList: [{
        'longitude': 120.139998,
        'latitude': 33.377631,
        'stationName': '盐城台站1',
        'stationAddress': 'xxxx'
      }, {
        'longitude': 120.339998,
        'latitude': 33.377631,
        'stationName': '盐城台站2',
        'stationAddress': 'xxxx'
      }]
    };
  },
  methods: {
    createMark (lng, lat, info, BMap, map) {
      let c = map
      console.log(c)
      const _marker = new BMap.Marker(new BMap.Point(lng, lat))
      _marker.addEventListener('mouseover', function () {
        var content = '<div>台站名称：' + info.stationName + '</div> ' + '<div>台站地址：' + info.stationAddress + '</div>'
        this.openInfoWindow(new BMap.InfoWindow(content))
      })
      return _marker
    },

    async handler ({ BMap, map }) {
      let mapStyle = { style: 'midnight' }
      map.setMapStyle(mapStyle)
      this.center.lng = 120.139998
      this.center.lat = 33.377631
      for (var i = 0, pointsLen = this.stationList.length; i < pointsLen; i++) {
        var marker = this.createMark(this.stationList[i].longitude, this.stationList[i].latitude, this.stationList[i], BMap, map)
        map.addOverlay(marker)
      }
    },
  }
};
</script>

<style lang="scss" scoped>
.bm-view {
  width: 6rem;
  height: 6rem;
}
</style>