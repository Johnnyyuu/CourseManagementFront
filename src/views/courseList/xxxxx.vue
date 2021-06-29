<!-- created by Johnny in 2021/6/16 -->
<template>
  <div class="main">
    <div style="margin: 10px 10px 0px 10px">
      <el-card>
        <div slot="header">Select Course</div>
        <course-selector></course-selector>
      </el-card>
    </div>
    <div style="margin: 10px 10px 0px 10px">
      <el-card>
        <time-table :CourseInfo="courseInfo"></time-table>
      </el-card>
    </div>
  </div>
</template>

<script>
// import { getList } from "@/api/table";
import "../../styles/main-container.scss";
import TimeTable from "../dashboard/components/timeTable";
import CourseSelector from "./components/courseSelector";
export default {
  // filters: {
  //   statusFilter(status) {
  //     const statusMap = {
  //       published: "success",
  //       draft: "gray",
  //       deleted: "danger",
  //     };
  //     return statusMap[status];
  //   },
  // },
  data() {
    return {
      // todo:
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
  components: {
    TimeTable,
    CourseSelector,
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {},
    // fetchData() {
    //   this.listLoading = true;
    //   getList().then((response) => {
    //     this.list = response.data.items;
    //     this.listLoading = false;
    //   });
    // },
  },
};
</script>

<style scoped>
</style>
