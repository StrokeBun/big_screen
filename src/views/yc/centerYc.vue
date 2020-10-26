<template>
  <div id="center">
    <div class="up">
      <div class="bg-color-black item" v-for="item in titleItem" :key="item.title">
        <p class="ml-3 colorBlue fw-b">{{item.title}}</p>
        <div>
          <dv-digital-flop :config="item.number" style="width:1.25rem;height:.625rem;" />
        </div>
      </div>
    </div>
    <div class="down">
      <div class="ranking bg-color-black" style="width: 100%">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2 mb-1">各市设备入库年度统计</span>
        <dv-scroll-ranking-board :config="ranking" style="width:100%;height:2.75rem" />
      </div>
<!--      <div class="percent">-->
<!--        <div class="item bg-color-black">-->
<!--          <span>今日任务通过率</span>-->
<!--          <CenterChart :id="rate[0].id" :tips="rate[0].tips" :colorObj="rate[0].colorData" />-->
<!--        </div>-->
<!--        <div class="item bg-color-black">-->
<!--          <span>今日任务达标率</span>-->
<!--          <CenterChart :id="rate[1].id" :tips="rate[1].tips" :colorObj="rate[1].colorData" />-->
<!--        </div>-->
<!--        <div class="water">-->
<!--          <dv-water-level-pond :config="water" style="height: 1.5rem" />-->
<!--        </div>-->
<!--      </div>-->
    </div>
  </div>
</template>

<script>
// import CenterChart from "@/components/echart/center/centerChartRate";

export default {
  data () {
    return {
      titleItem: [
        {
          title: "今年设备入库数",
          number: {
            number: [120],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "本月设备入库数",
          number: {
            number: [18],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "今日设备入库数",
          number: {
            number: [2],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "今年设备出库数",
          number: {
            number: [106],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "本月设备出库数",
          number: {
            number: [14],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "今日设备出库数",
          number: {
            number: [2],
            toFixed: 1,
            content: "{nt}"
          }
        }
      ],
      ranking: {
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
        ],
        carousel: "single",
        unit: ""
      },
      water: {
        data: [24, 45],
        shape: "roundRect",
        formatter: "{value}%",
        waveNum: 3
      },
      // 通过率和达标率的组件复用数据
      rate: [
        {
          id: "centerRate1",
          tips: 60,
          colorData: {
            textStyle: "#3fc0fb",
            series: {
              color: ["#00bcd44a", "transparent"],
              dataColor: {
                normal: "#03a9f4",
                shadowColor: "#97e2f5"
              }
            }
          }
        },
        {
          id: "centerRate2",
          tips: 40,
          colorData: {
            textStyle: "#67e0e3",
            series: {
              color: ["#faf3a378", "transparent"],
              dataColor: {
                normal: "#ff9800",
                shadowColor: "#fcebad"
              }
            }
          }
        }
      ]
    };
  },
  components: {
    // CenterChart
    // centerChart1,
    // centerChart2
  }
};
</script>

<style lang="scss" scoped>
#center {
  display: flex;
  flex-direction: column;
  .up {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 0.0625rem;
      padding-top: 0.2rem;
      margin-top: 0.1rem;
      width: 32%;
      height: 0.875rem;
    }
  }
  .down {
    padding: 0.07rem 0.05rem;
    padding-bottom: 0;
    width: 100%;
    display: flex;
    height: 3.1875rem;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 0.0625rem;
    }
    .ranking {
      padding: 0.125rem;
      width: 59%;
    }
    .percent {
      width: 40%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 50%;
        height: 1.5rem;
        span {
          margin-top: 0.0875rem;
          display: flex;
          justify-content: center;
        }
      }
      .water {
        width: 100%;
      }
    }
  }
}
</style>