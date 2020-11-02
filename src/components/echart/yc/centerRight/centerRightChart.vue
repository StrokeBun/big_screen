<template>
  <div id="centreRightChart">
    <div id="centreRight2Chart1" class="monthChar"></div>
    <div id="centreRight2Chart2" class="monthChar"></div>
  </div>
</template>

<script>
import echartMixins from "@/utils/resizeMixins";

export default {
  data() {
    return {
      alertMonthStatisticsByType: [
        { value: 257, name: '台站环境' },
        { value: 390, name: '地震测量' },
        { value: 620, name: '网络错误' }
      ],
      alertMonthStatisticsByLevel: [
        { name: '严重警报', value: 25},
        { name: '一般警报', value: 520},
        { name: '重要警报', value: 134}
      ]
    };
  },
  mixins: [echartMixins],
  mounted() {
    this.draw();
    this.draw2();
  },
  methods: {
    draw() {
      this.chart = this.$echarts.init(document.getElementById("centreRight2Chart1"));
      var option = {
        title: {
          text: '当月警报分类统计',
          x: 'center',
          textStyle: {
            fontSize: 14,
            color: '#ffffff'
          }
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
          orient: 'horizontal',
          left: 'center',
          top: '13%',
          textStyle: {
            fontSize: 12,
            color: '#ffffff'
          },
          data: ['台站环境', '地震测量', '网络错误']
        },
        series: [
          {
            name: '警报类型',
            type: 'pie',
            radius: '55%',
            center: ['50%', '60%'],
            label: {
              show: false
            },
            labelLine: {
              show: false
            },
            data: this.alertMonthStatisticsByType,
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              }
            }
          }
        ]
      }
      this.chart.setOption(option);
    },

    draw2() {
      this.chart = this.$echarts.init(document.getElementById("centreRight2Chart2"));
      var option = {
        title: {
          text: '当月警报级别统计',
          x: 'center',
          textStyle: {
            fontSize: 14,
            color: '#ffffff'
          }
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
          orient: 'horizontal',
          left: 'center',
          top: '13%',
          textStyle: {
            fontSize: 12,
            color: '#ffffff'
          },
          data: ['一般警报', '重要警报', '严重警报']
        },
        series: [
          {
            name: '警报级别',
            type: 'pie',
            radius: '50%',
            center: ['50%', '60%'],
            label: {
              show: false
            },
            labelLine: {
              show: false
            },
            data: this.alertMonthStatisticsByLevel,
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              }
            }
          }
        ]
      }
      this.chart.setOption(option);
    }
  }
};
</script>

<style lang="scss" scoped>
.monthChar {
  width:4.4rem; height: 2.60rem;margin-top: 0.1rem
}
</style>