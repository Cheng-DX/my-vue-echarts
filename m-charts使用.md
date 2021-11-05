## myCharts.vue:一个封装图像全屏、数据表格的vue-echarts组件

#### 0.使用环境

- vue2
- vue-echarts 5.0 (***npm install vue-echarts @5.9.0***
- Echarts 5.0以下 
- 使用：

```javascript
import MyEcharts from './echarts/myEcharts.vue'
Vue.component('m-chart',MyEcharts)
```

```vue
<div style="height: 20vh">
    <m-chart :option="option" mode="light"/>
</div>
```

- 属性说明：

  - option：同vue-echarts的options，将自动装入<v-chart>的options属性

  - mode：mode为“light”时切换为亮色主题；mode不赋值或其他值时，m-chart为暗色主题，即线条颜色偏明亮
  - 该组件内部的v-chart默认尺寸为100%×100%，故建议在外层指定高度（*vue-echarts6.0已默认v-chart尺寸为100%×100%*）

#### 1. 子组件1：echartsFull.vue

- 默认全屏显示
- 默认替换原option设定的grid属性
- 默认替换标题
- 默认为x轴添加dataZoom组件

#### 2. 子组件2：echartsData.vue

- 默认title为“数据视图”
- 支持多series
- 支持多y轴
- 支持多渠道获取表头名称

#### 3.效果

![image-20211105235342768](C:\Users\猫丞\Desktop\9M\image-20211105235342768.png)

![image-20211105235426977](C:\Users\猫丞\Desktop\9M\image-20211105235426977.png)

![image-20211105235523569](C:\Users\猫丞\Desktop\9M\image-20211105235523569.png)
