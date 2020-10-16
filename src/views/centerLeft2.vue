<template>
  <div id="centreLeft2">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2">各市设备数目统计</span>
      </div>
      <div class="d-flex jc-center body-box" style=" margin-top: 0;">
        <dv-capsule-chart :config="config" style="width: 100%;height:5rem" />
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      config: {
        data: [
          {
            name: "南京",
            value: 167
          },
          {
            name: "镇江",
            value: 67
          },
          {
            name: "扬州",
            value: 30
          },
          {
            name: "泰州",
            value: 25
          },
          {
            name: "南通",
            value: 60
          },
          {
            name: "常州",
            value: 76
          },
          {
            name: "无锡",
            value: 69
          },
          {
            name: "苏州",
            value: 110
          },
          {
            name: "盐城",
            value: 220
          },
          {
            name: "淮安",
            value: 23
          },
          {
            name: "宿迁",
            value: 45
          },
          {
            name: "徐州",
            value: 60
          },
          {
            name: "连云港",
            value: 77
          }
        ]
      }
    };
  },
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
#centreRight2 {
  padding: 0.0625rem;
  height: 5rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
  .bg-color-black {
    padding: 0.0625rem;
    height: 5.0625rem;
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