<template>
  <div id="centreRight1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="chart-line"></icon>
        </span>
        <div class="d-flex">
          <span class="fs-xl text mx-2">今日台站报警情况</span>
        </div>
      </div>
      <div class="d-flex jc-center body-box">
        <dv-capsule-chart :config="alarm" style="width: 100%;height:1.8rem" />
        <dv-capsule-chart :config="solve" style="width: 100%;height:1.8rem" />
        <div class="d-flex" style="margin-top: 0.1rem; margin-bottom: 0.1rem">
          <span class="fs-xl text mx-2" style="text-align: center">处理进度</span>
        </div>
        <dv-percent-pond :config="config" style="width:2rem;height:1rem;left: 30%" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      alarm: {
        data: [
          {
            name: "台站环境",
            value: 167
          },
          {
            name: "地震测量",
            value: 67
          },
          {
            name: "网络故障",
            value: 123
          }
        ]
      },
      solve: {
        data: [
          {
            name: "警报数量",
            value: 300
          },
          {
            name: "已解决",
            value: 240
          },
          {
            name: "未处理",
            value: 60
          }
        ]
      },
      config: {
        value: 80
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
  height: 6rem;
  width: 6.6rem;
  border-radius: 0.0625rem;
  .bg-color-black {
    height: 5.7rem;
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