<template>
  <div>
    <tiny-baidu-map :options="options"></tiny-baidu-map>
  </div>
</template>

<script lang="jsx">
import { HuichartsBmap } from '@opentiny/vue'

export default {
  components: {
    TinyBaiduMap: HuichartsBmap
  },
  data() {
    return {
      options: {
        key: 'oBvDtR6nzWtVchkY4cLHtnah1VVZQKRK',
        url: 'https://api.map.baidu.com/api', // 百度地图接口的url地址
        v: '1.4.3',
        bmap: {
          resizeEnable: true,
          center: [120.14322240845, 30.236064370321],
          zoom: 10
        },
        tooltip: {
          show: true
        },
        series: [
          {
            type: 'scatter',
            coordinateSystem: 'bmap',
            data: [
              [120, 30, 1] // 经度，纬度，value...
            ]
          }
        ]
      }
    }
  }
}
</script>
