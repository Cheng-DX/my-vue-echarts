<template>
  <el-dialog
    top="5vh"
    width="80%"
    :modal="true"
    center
    title="数据视图"
    append-to-body
    :visible.sync="dialogVisible"
    :modal-append-to-body="false"
    @closed="deleteData"
  >
    <el-table :data="tableData" style="width: 100%" height="75vh">
      <el-table-column type="index" width="60" sortable> </el-table-column>
      <el-table-column
        v-for="(item, index) in labels"
        :key="index"
        :prop="item.prop"
        :label="item.label"
        sortable
        min-width="100"
        align="center"
      ></el-table-column>
    </el-table>
  </el-dialog>
</template>

<script>
export default {
  data() {
    return {
      dialogVisible: false,
      tableData: [],
      labels: [],
      title: "",
    };
  },
  methods: {
    deleteData() {
      this.tableData = [];
    },
    show(val) {
      this.tableData = [];
      this.labels = [];
      this.title = val.title;
      this.labels.push({ prop: "-1", label: val.xAxis[0].name });
      for (let i = 0; i < val.series.length; i++) {
        let obj = {};
        obj["prop"] = i + "";
        let currentLabel = '';
        if(val.series[i].name === undefined){
          if(val.series[i].yAxisIndex === undefined){
            currentLabel = val.yAxis[0].name;
          }else{
            currentLabel = val.yAxis[val.series[i].yAxisIndex].name;
          }
        }else{
          currentLabel = val.series[i].name;
        }
        obj["label"] = currentLabel;
        this.labels.push(obj);
      }
      for (let i = 0; i < val.xAxis[0].data.length; i++) {
        let obj = {};
        obj["-1"] = val.xAxis[0].data[i];
        for (let j = 0; j < val.series.length; j++) {
          let prop = j + "";
          obj[prop] = val.series[j].data[i];
        }
        this.tableData.push(obj);
      }
      this.dialogVisible = true;
    },
  },
};
</script>

<style scoped>
::-webkit-scrollbar {
  width: 7px;
}
::-webkit-scrollbar-thumb {
  background-color: #13010167;
  border-radius: 3px;
}
</style>

