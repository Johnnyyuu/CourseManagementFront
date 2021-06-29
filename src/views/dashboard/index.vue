<!-- created by Johnny in 2021/6/15 -->
<template>
  <div class="dashboard-container">
    <!-- <div class="dashboard-text">Hello, {{ name }}</div> -->
    <div class="info-container">
      <el-card class="infoCard">
        <div slot="header" class="">
          <span>Program Overview</span>
        </div>
        <ratio-chart :RatioInfo="ratioInfo"></ratio-chart>
      </el-card>
      <el-card class="infoCard">
        <div slot="header">
          <span>Key Sessional Dates</span>
        </div>
        <key-session></key-session>
      </el-card>
    </div>
    <el-card style="border-radius: 10px; margin-right: 20px">
      <div slot="header">
        <span>Course TimeTable</span>
      </div>
      <time-table :CourseInfo="courseInfo"></time-table>
    </el-card>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import RatioChart from "./components/ratioChart";
import TimeTable from "./components/timeTable.vue";
import KeySession from "./components/keySession.vue";

export default {
  name: "Dashboard",

  components: {
    RatioChart,
    TimeTable,
    KeySession,
  },

  data() {
    return {
      courseList: null,
      // Info for Program Overview, todo: get from interface
      ratioInfo: {
        courseCompleted: 7,
        courseTodo: 2,
        techUndo: 1,
        NontechUndo: 0,
      },
      courseInfo: [
        [{}, {}, {}, {}, {}],
        [{}, {}, {}, {}, { name: "ECE1779", color: 2 }],
        [{}, {}, {}, {}, {}],
        [{}, { name: "ECE1762", color: 1 }, {}, {}, {}],
        [{ name: "APS1022", color: 3 }, {}, {}, {}, {}],
        [{}, {}, {}, {}, {}],
        [{}, {}, { name: "ECE1762", color: 1 }, {}, {}],
      ],
    };
  },
  computed: {
    ...mapGetters(["name"]),
  },
};
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 20px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
    margin-bottom: 20px;
  }
}

.info-container {
  display: flex;
  justify-content: space-around;
}
::v-deep .el-card__body {
  padding: 0;
}
.infoCard {
  width: 50%;
  margin-right: 20px;
  margin-bottom: 20px;
  border-radius: 10px;
}
.infoCard:last-of-type {
  margin-right: 20px;
}
</style>
