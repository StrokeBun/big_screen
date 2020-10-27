<template>
  <div id="centreRight2">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2">当月告警统计</span>
      </div>
      <div class="d-flex jc-center body-box" style=" margin-top: 0;">
        <centerRightChart />
      </div>
    </div>
  </div>
</template>

<script>
import centerRightChart from "_c/echart/yc/centerRight/centerRightChart";
export default {
  data() {
    return {
    };
  },
  components: { centerRightChart },
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
#centreRight2 {
  padding: 0.0625rem;
  height: 6rem;
  width: 5.5rem;
  border-radius: 0.0625rem;
  .bg-color-black {
    padding: 0.0625rem;
    height: 6rem;
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