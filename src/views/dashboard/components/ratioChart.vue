<!-- created by Johnny in 2021/6/15 -->
<template>
  <div>
    <el-col :span="16"
      ><div id="myChart" style="width: 100%; height: 400px"></div
    ></el-col>
    <el-col :span="8" style="font-size: 15px">
      <div style="margin: 20px 0; font-size: 18px"></div>
      <div>
        <el-row style="margin: 30px 10px 15px 0"
          >Still need {{ techUndo }} Technical Class</el-row
        >
        <el-button v-if="techUndo !== 0" type="primary">Add One</el-button>
        <el-button v-if="techUndo === 0" disabled>Completed</el-button>
        <el-row style="margin: 35px 10px 15px 0"
          >Still need {{ NontechUndo }} Nontechnical Class</el-row
        >
        <el-button v-if="NontechUndo !== 0">Add One</el-button>
        <el-button v-if="NontechUndo === 0" disabled>Completed</el-button>
      </div>
      <el-row style="margin: 50px 10px 15px 0">
        Statuses:<el-tag type="success" style="margin-left: 5px"
          >Registed</el-tag
        ></el-row
      >
    </el-col>
  </div>
</template>

<script>
export default {
  name: "RatioChart",
  props: {
    RatioInfo: {},
  },
  data() {
    return {
      courseCompleted: 7,
      courseTodo: 2,
      techUndo: 1,
      NontechUndo: 0,
    };
  },

  created() {
    let cur_info = this.RatioInfo;
    this.courseCompleted = cur_info.courseCompleted;
    this.courseTodo = cur_info.courseTodo;
    this.techUndo = cur_info.techUndo;
    this.NontechUndo = cur_info.NontechUndo;
  },
  mounted() {
    this.drawChart();
  },
  methods: {
    drawChart() {
      let myChart = this.$echarts.init(document.getElementById("myChart"));
      myChart.setOption({
        tooltip: {
          trigger: "item",
        },
        legend: {
          top: "5%",
          left: "center",
        },
        series: [
          {
            type: "pie",
            radius: ["40%", "70%"],
            avoidLabelOverlap: false,
            itemStyle: {
              borderRadius: 10,
              borderColor: "#fff",
              borderWidth: 2,
            },
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: "16",
                fontWeight: "bold",
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: this.courseCompleted, name: "Finished" },
              { value: this.courseTodo, name: "Unfinished" },
            ],
          },
        ],
      });
    },
  },
};
</script>

<style scoped>
.div {
  margin: 0;
  padding: 0;
}
</style>
