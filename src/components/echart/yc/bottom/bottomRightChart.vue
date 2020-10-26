<template>
  <div>
    <div id="bottomRightChart" style="width:11.25rem;height:6rem;"></div>
  </div>
</template>

<script>
import echartMixins from "@/utils/resizeMixins";

export default {
  data() {
    return {
      chart: null
    };
  },
  mounted() {
    this.draw();
  },
  mixins: [echartMixins],
  methods: {
    charTimg() {
      setInterval(() => {
        this.draw();
      }, 6000);
    },
    draw() {
      // 基于准备好的dom，初始化echarts实例
      this.chart = this.$echarts.init(document.getElementById("bottomRightChart"));
      //  ----------------------------------------------------------------
      // 数据
      let dateBase = new Date();
      let year = dateBase.getFullYear();
      let dottedBase = +dateBase + 1000 * 3600 * 24;
      let weekCategory = [];

      let maxData = 12000;
      let weekMaxData = [];
      let weekLineData = [];

      // 周数据
      for (let i = 0; i < 30; i++) {
        // 日期
        var date = new Date((dottedBase -= 1000 * 3600 * 24));
        weekCategory.unshift([date.getMonth() + 1, date.getDate()].join("/"));

        // 折线图数据
        weekMaxData.push(maxData);
        var distance = Math.round(Math.random() * 11000 + 500);
        weekLineData.push(distance);
      }

      // 颜色设置
      let color = {
        linearYtoG: {
          type: "linear",
          x: 0,
          y: 0,
          x2: 1,
          y2: 1,
          colorStops: [
            {
              offset: 0,
              color: "#f5b44d"
            },
            {
              offset: 1,
              color: "#28f8de"
            }
          ]
        },
        linearGtoB: {
          type: "linear",
          x: 0,
          y: 0,
          x2: 1,
          y2: 0,
          colorStops: [
            {
              offset: 0,
              color: "#43dfa2"
            },
            {
              offset: 1,
              color: "#28f8de"
            }
          ]
        },
        linearBtoG: {
          type: "linear",
          x: 0,
          y: 0,
          x2: 1,
          y2: 0,
          colorStops: [
            {
              offset: 0,
              color: "#1c98e8"
            },
            {
              offset: 1,
              color: "#28f8de"
            }
          ]
        },
        areaBtoG: {
          type: "linear",
          x: 0,
          y: 0,
          x2: 0,
          y2: 1,
          colorStops: [
            {
              offset: 0,
              color: "rgba(35,184,210,.2)"
            },
            {
              offset: 1,
              color: "rgba(35,184,210,0)"
            }
          ]
        }
      };
      let option = {
        title: {
          text: "",
          textStyle: {
            color: "#D3D6DD",
            fontSize: 24,
            fontWeight: "normal"
          },
          subtext: year + "/" + weekCategory[6],
          subtextStyle: {
            color: "#fff",
            fontSize: 16
          },
          top: 20,
          left: 400
        },
        tooltip: {
          trigger: "item"
        },
        grid: {
          left: 90,
          right: 80,
          bottom: 40,
          top: "20%"
        },
        xAxis: {
          type: "category",
          position: "bottom",
          axisLine: true,
          axisLabel: {
            color: "rgba(255,255,255,.8)",
            fontSize: 12
          },
          data: weekCategory
        },
        // 下方Y轴
        yAxis: {
          name: "工单数",
          nameLocation: "end",
          nameGap: 24,
          nameTextStyle: {
            color: "rgba(255,255,255,.5)",
            fontSize: 14
          },
          max: maxData,
          splitNumber: 4,

          axisLine: {
            lineStyle: {
              opacity: 0
            }
          },
          splitLine: {
            show: true,
            lineStyle: {
              color: "#fff",
              opacity: 0.1
            }
          },
          axisLabel: {
            color: "rgba(255,255,255,.8)",
            fontSize: 12
          }
        },
        series: [
          {
            name: "",
            type: "line",
            smooth: true,
            symbol: "emptyCircle",
            symbolSize: 8,
            itemStyle: {
              normal: {
                color: "#fff"
              }
            },
            lineStyle: {
              normal: {
                color: color.linearBtoG,
                width: 3
              }
            },
            areaStyle: {
              normal: {
                color: color.areaBtoG
              }
            },
            data: weekLineData,
            lineSmooth: true,
            markLine: {
              silent: true,
              data: [
                {
                  type: "average",
                  name: "平均"
                }
              ],
              precision: 0,
              label: {
                normal: {
                  formatter: "平均: \n {c}"
                }
              },
              lineStyle: {
                normal: {
                  color: "rgba(248,211,81,.7)"
                }
              }
            },
            tooltip: {
              position: "top",
              formatter: "{c}",
              backgroundColor: "rgba(28,152,232,.2)",
              padding: 6
            }
          },
          {
            name: "占位背景",
            type: "bar",
            itemStyle: {
              normal: {
                show: true,
                color: "#000",
                opacity: 0
              }
            },
            silent: true,
            barWidth: "50%",
            data: weekMaxData,
            animation: false
          }
        ]
      };
      this.chart.setOption(option);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>