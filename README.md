## myCharts.vue:一个封装图像全屏、数据表格、支持快速模式的vue-echarts组件

### 使用环境

- vue2
- vue-echarts 
- Echarts
- ElementUI : 可选 内置的全屏使用的是elementui,可自行更换

### 安装
```shell
npm install echarts vue-echarts
npm install element-ui --save # 可选
```
```javascript
// in main.js
import VueECharts from 'vue-echarts'
// 配置项
import '...echarts.js'
import dcharts from '...dcharts.vue'

Vue.component('v-chart', VueECharts)
Vue.component('d-chart', dcharts)

```
### 使用：
```vue
<div style="height: 20vh;width: 50vw">
    <d-chart/>
</div>
```

### props：

|prop|type|default|description|
| :----------: | :--: | :-----: |:--:|
|option|Object|null|native option in echart
|title|string|'DCHART'|title of chart
|mode|string|'light'|color mode of chart,light or dark
|disabled-full-screen|boolean|false|disable fullscreen tool
|disabled-table|boolean|false|disable table tool
|fast-mode|boolean|false|fast mode of chart,you can set the data only to create chart while this property is true
|x-data|Array|[]|xAxis data of chart
|series|Array or Object|null|series data of chart,see echart's series
|type|string|'line'|chart type,this property will work only when the item in series does not have property 'type'
|label|boolean|false|show label
|label-position|string|'top'|label position

### 示例
- option示例见[option.vue](./templates/optionDemo.vue)
- fast-mode示例见[fastMode.vue](./templates/fastMode.vue)
