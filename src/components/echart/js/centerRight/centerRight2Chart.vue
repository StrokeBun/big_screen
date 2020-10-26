<template>
  <div>
    <div id="centreRight2Chart1" style="width:3.25rem; height: 2.60rem;margin-top: 0.4rem"></div>
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
  mixins: [echartMixins],
  mounted() {
    this.draw();
  },
  methods: {
    draw() {
      // 基于准备好的dom，初始化echarts实例
      this.chart = this.$echarts.init(document.getElementById("centreRight2Chart1"));
      //  ----------------------------------------------------------------
      let alertNum = [
        [167, 67, 123]
      ];

      let lineStyle = {
        normal: {
          width: 1,
          opacity: 0.5
        }
      };

      let option = {
        radar: {
          indicator: [
            { name: "台站环境", max: 180 },
            { name: "地震测量", max: 150 },
            { name: "网络故障", max: 180 }
          ],
          shape: "circle",
          splitNumber: 5,
          name: {
            textStyle: {
              color: "rgb(238, 197, 102)"
            }
          },
          splitLine: {
            lineStyle: {
              color: [
                "rgba(238, 197, 102, 1)",
                "rgba(238, 197, 102, 0.8)",
                "rgba(238, 197, 102, 0.6)",
                "rgba(238, 197, 102, 0.4)",
                "rgba(238, 197, 102, 0.2)",
                "rgba(238, 197, 102, 0.1)"
              ].reverse()
            }
          },
          splitArea: {
            show: false
          },
          axisLine: {
            lineStyle: {
              color: "rgba(238, 197, 102, 0.5)"
            }
          }
        },
        series: [
          {
            name: "告警数量",
            type: "radar",
            lineStyle: lineStyle,
            data: alertNum,
            symbol: "none",
            itemStyle: {
              normal: {
                color: "#00FF7F"
              }
            },
            areaStyle: {
              normal: {
                opacity: 0.05
              }
            }
          }
        ]
      };
      this.chart.setOption(option);
    }
  }
};
</script>

<style lang="scss" scoped>
#centreRight2Chart1 {
  margin: 0 auto;
}
</style>