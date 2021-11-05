<template>
  <div class="vchart border border-info rounded-lg">
    <v-chart
      :options="option"
      style="height: 100%; width: 100%"
      :key="1"
      ref="echart"
      :autoresize="true"
    />
    <echarts-full ref="echartsFull" />
    <echarts-data ref="echartsData" />
  </div>
</template>

<script>
import echartsFull from "../echarts/echartsFull.vue";

export default {
  components: { echartsFull },
  props: {
    option: Object,
    mode: String,
  },
  mounted() {
    if (this.option) {
      this.draw()
    }
  },
  created() {
    if(this.option) {
      this.draw()
    }
  },
  watch: {
    option: function () {
      this.draw();
    },
  },
  data() {
    return {};
  },
  methods: {
    draw() {
      let imageColor = "#01244b";

      if (this.mode === "light") {
        imageColor = "transperent";
      }
      this.option['toolbox'] = {
        feature: {
          restore: {},
          saveAsImage: {
            name: this.title,
            backgroundColor: imageColor,
            pixelRatio: 5,
          },
          myToolFull: {
            show: true,
            title: "全屏查看",
            icon: "path://M733.549304 0l116.434359 116.23452-226.402521 226.40252 57.053835 57.068109 226.459617-226.445342 120.616689 120.41685V0H733.549304zM689.513507 619.855586l-57.068108 57.068109 224.232847 224.232847-122.64362 122.843458h293.676657V729.838022l-114.007751 114.207588-224.190025-224.190024zM338.197775 404.144414l57.068109-57.068109L171.033037 122.843458 293.676657 0H0v294.161978l114.022025-114.207588 224.17575 224.190024zM347.076305 624.294851L120.616689 850.754468 0 730.323343v293.676657h294.161978l-116.420084-116.23452 226.40252-226.40252-57.068109-57.068109z",
            onclick: (e) => {
              this.$refs.echartsFull.show(e.getOption());
            },
          },
          myToolData: {
            show: true,
            title: "查看数据",
            icon: "M426.666667 427.52h213.333333V896h-213.333333V427.52zM725.333333 896h128c46.933333 0 85.333333-38.4 85.333334-85.333333v-384h-213.333334v469.333333z m128-768H213.333333c-46.933333 0-85.333333 38.4-85.333333 85.333333v128h810.666667V213.333333c0-46.933333-38.4-85.333333-85.333334-85.333333zM128 810.666667c0 46.933333 38.4 85.333333 85.333333 85.333333h128V426.666667H128v384z",
            onclick: (e) => {
              this.$refs.echartsData.show(e.getOption());
            },
          },
        },
      };
    },
  },
};
</script>

<style scoped>
.vchart {
  height: 100%;
  width: 100%;
  color: lightgray;
}
</style>>

