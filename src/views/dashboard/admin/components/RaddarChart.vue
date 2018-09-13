<template>
  <div :class="className" :style="{height:height,width:width}"/>
</template>

<script>
import echarts from 'echarts'
require('echarts/theme/macarons') // echarts theme
import { debounce } from '@/utils'

const animationDuration = 3000

export default {
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '300px'
    }
  },
  data() {
    return {
      chart: null
    }
  },
  mounted() {
    this.initChart()
    this.__resizeHandler = debounce(() => {
      if (this.chart) {
        this.chart.resize()
      }
    }, 100)
    window.addEventListener('resize', this.__resizeHandler)
  },
  beforeDestroy() {
    if (!this.chart) {
      return
    }
    window.removeEventListener('resize', this.__resizeHandler)
    this.chart.dispose()
    this.chart = null
  },
  methods: {
    initChart() {
      this.chart = echarts.init(this.$el, 'macarons')

      this.chart.setOption({
        tooltip: {
          trigger: 'axis',
          axisPointer: { // 坐标轴指示器，坐标轴触发有效
            type: 'shadow' // 默认为直线，可选为：'line' | 'shadow'
          }
        },
        radar: {
          radius: '66%',
          center: ['50%', '42%'],
          splitNumber: 8,
          splitArea: {
            areaStyle: {
              color: 'rgba(127,95,132,.3)',
              opacity: 1,
              shadowBlur: 45,
              shadowColor: 'rgba(0,0,0,.5)',
              shadowOffsetX: 0,
              shadowOffsetY: 15
            }
          },
          indicator: [
            { name: 'Jakarta Timur', max: 10000 },
            { name: 'Jakarta Barat', max: 20000 },
            { name: 'Jakarta Selatan', max: 20000 },
            { name: 'Jakarta Pusat', max: 20000 },
            { name: 'Jakarta Utara', max: 20000 },
            { name: 'Kep. Seribu', max: 20000 }
          ]
        },
        legend: {
          left: 'center',
          bottom: '10',
          data: ['Putra Nababan', 'Wiryanti Sukamdani', 'William Yani', 'Mirza R. Kesuma', 'Andrie T. Utama', 'S. T. Debora Tampubolon']
        },
        series: [{
          type: 'radar',
          symbolSize: 0,
          areaStyle: {
            normal: {
              shadowBlur: 13,
              shadowColor: 'rgba(0,0,0,.2)',
              shadowOffsetX: 0,
              shadowOffsetY: 10,
              opacity: 1
            }
          },
          data: [
            {
              value: [5000, 7000, 12000, 11000, 15000, 14000],
              name: 'Putra Nababan'
            },
            {
              value: [4000, 9000, 15000, 15000, 13000, 11000],
              name: 'Wiryanti Sukamdani'
            },
            {
              value: [5500, 11000, 12000, 15000, 12000, 12000],
              name: 'William Yani'
            },
            {
              value: [6000, 7500, 11000, 9000, 7000, 13000],
              name: 'Mirza R. Kesuma'
            },
            {
              value: [8000, 9500, 15500, 6000, 11000, 8000],
              name: 'Andrie T. Utama'
            },
            {
              value: [4500, 10000, 13000, 3000, 2000, 6000],
              name: 'S. T. Debora Tampubolon'
            }
          ],
          animationDuration: animationDuration
        }]
      })
    }
  }
}
</script>
