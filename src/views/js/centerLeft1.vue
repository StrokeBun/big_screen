<template>
  <div id="centreLeft1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="chart-bar"></icon>
        </span>
        <div class="d-flex">
          <span class="fs-xl text mx-2">设备统计</span>
          <dv-decoration-3 style="width:1.25rem;height:.25rem; position:relative;top:-.0375rem;" />
        </div>
      </div>
      <div class="d-flex jc-center">
        <CentreLeft1Chart />
      </div>
      <!-- 4个主要的数据 -->
      <div class="bottom-data">
        <div class="item-box" v-for="(item,index) in numberData" :key="index">
          <div class="d-flex">
            <span class="coin"></span>
            <dv-digital-flop :config="item.number" style="width:2.5rem;height:.625rem;" />
          </div>
          <p class="text" style="text-align: center;">
            {{item.text}}
            <span class="colorYellow"></span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CentreLeft1Chart from "_c/echart/js/centerLeft/centreLeft1Chart";
export default {
  data() {
    return {
      config: {
        lineWidth: 30,
        activeRadius: "80%",
        radius: "75%",
        activeTimeGap: 2000,
        // data: [
        //   {
        //     name: "周口",
        //     value: 55
        //   },
        //   {
        //     name: "南阳",
        //     value: 120
        //   },
        //   {
        //     name: "西峡",
        //     value: 78
        //   },
        //   {
        //     name: "驻马店",
        //     value: 66
        //   },
        //   {
        //     name: "新乡",
        //     value: 80
        //   }
        // ]
      },
      numberData: [
        {
          number: {
            number: [1600],
            content: "{nt}"
          },
          text: "正常使用数量"
        },
        {
          number: {
            number: [1680],
            // toFixed: 1,
            content: "{nt}"
          },
          text: "总计数量"
        },
        {
          number: {
            number: [40],
            content: "{nt}"
          },
          text: "报废数量"
        },
        {
          number: {
            number: [40],
            content: "{nt}"
          },
          text: "维修数量"
        }
      ]
    };
  },
  components: {
    CentreLeft1Chart
  },
  mounted() {
    this.changeTiming();
  },
  methods: {
    changeTiming() {
      setInterval(() => {
        // this.changeNumber();
      }, 3000);
    },
    changeNumber() {
      this.numberData.forEach((item, index) => {
        item.number.number[0] += ++index;
        item.number = { ...item.number };
      });
    }
  }
};
</script>

<style lang="scss">
#centreLeft1 {
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
  .chart-box {
    margin-top: 0.2rem;
    width: 2.125rem;
    height: 2.125rem;
    .active-ring-name {
      padding-top: 0.125rem;
    }
  }

  .bottom-data {
    .item-box {
      float: right;
      position: relative;
      width: 50%;
      color: #d3d6dd;
      // 金币
      .coin {
        position: absolute;
        left: 0.1rem;
        top: 0.2125rem;
        font-size: 0.25rem;
        color: #ffc107;
      }
      .colorYellow {
        color: yellowgreen;
      }
    }
  }
}
</style>