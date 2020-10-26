<template>
  <div id="bottomLeftChart" style="width:12rem;height:6.25rem;">
    <div id="station-1" class="station-show">
      <img :src="require('./station.png')" style="width: 100%" />
      <div class="d-flex jc-center body-box">
        <dv-scroll-board :config="config1" style="width:4rem;height:3rem" />
      </div>
    </div>
    <div id="station-2" class="station-show">
      <img :src="require('./station.png')" style="width: 100%" />
      <div class="d-flex jc-center body-box">
        <dv-scroll-board :config="config1" style="width:4rem;height:3rem" />
      </div>
    </div>
  </div>
</template>

<script>
import echartMixins from "@/utils/resizeMixins";
export default {
  data() {
    return {
      config1: {
        header: ["台站", "报警原因", "是否处理"],
        data: [
          ["台站1", "温度过高", "否"]
        ],
        rowNum: 7, //表格行数
        headerHeight: 35,
        headerBGC: "#0f1325", //表头
        oddRowBGC: "#0f1325", //奇数行
        index: true,
        columnWidth: [50],
        align: ["center"]
      },
      config2: {
        header: ["台站", "报警原因", "是否处理"],
        data: [
          ["台站2", "网络异常", "否"]
        ],
        rowNum: 7, //表格行数
        headerHeight: 35,
        headerBGC: "#0f1325", //表头
        oddRowBGC: "#0f1325", //奇数行
        index: true,
        columnWidth: [50],
        align: ["center"]
      }
    };
  },
  mixins: [echartMixins],
  mounted() {
  },
  methods: {
  }
};
</script>
<style lang="scss" scoped>
.station-show {
  padding: 0.5rem 0.5rem;
  width:5.7rem;
  height: 5.25rem;
  float: left;
  background-image: url('./border.png');
  background-size: 100% 100%;
  background-position: center;
}
</style>