<template>
  <div id="centreRight1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="chart-line"></icon>
        </span>
        <div class="d-flex">
          <span class="fs-xl text mx-2">台站报警情况</span>
        </div>
      </div>
      <div class="d-flex jc-center body-box">
        <dv-scroll-board :config="config" style="width:4rem;height:4.28rem" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      config: {
        header: ["台站", "原因", "是否处理"],
        data: [
          ["台站1", "台站环境", "<span  class='colorGrass'>是</span>"],
          ["台站2", "台站环境", "<span  class='colorRed'>否</span>"],
          ["台站3", "地震测量", "<span  class='colorGrass'>是</span>"],
          ["台站4", "地震测量", "<span  class='colorGrass'>是</span>"],
          ["台站5", "网络错误", "<span  class='colorGrass'>否</span>"],
          ["台站6", "网络错误", "<span  class='colorGrass'>是</span>"],
          ["台站7", "网络错误", "<span  class='colorGrass'>是</span>"]
        ],
        rowNum: 7, //表格行数
        headerHeight: 35,
        headerBGC: "#0f1325", //表头
        oddRowBGC: "#0f1325", //奇数行
        evenRowBGC: "#171c33", //偶数行
        index: true,
        columnWidth: [50],
        align: ["center"]
      }
    };
  },
  components: {},
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
#centreRight1 {
  padding: 0.2rem;
  height: 5.125rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
  .bg-color-black {
    height: 4.8125rem;
    border-radius: 0.125rem;
  }
  .text {
    color: #c3cbde;
  }
  .body-box {
    border-radius: 0.125rem;
    overflow: hidden;
  }
}
</style>