<!-- created by Johnny in 2021/6/15 -->

<template>
  <!-- eslint-disable -->
  <div class="main_container">
    <table class="main_table">
      <thead>
        <tr>
          <th v-for="(item, key) in weeks" style="border: 0">
            {{ item }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, index) in CourseInfo">
          <th>{{ timePeriods[index] }}</th>
          <th v-for="(item, index) in row">
            <course-card
              :CourseName="item.name"
              :Color="item.color"
            ></course-card>
          </th>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import CourseCard from "./courseCard.vue";
export default {
  name: "TimeTable",
  props: {
    CourseInfo: {
      type: Array,
    },
  },
  components: {
    CourseCard,
  },
  data() {
    return {
      weeks: ["", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      timePeriods: ["9:00", "10:00", "11:00", "12:00", "1:00", "2:00", "3:00"],
    };
  },

  created() {
    this.courseInfo = this.CourseInfo;
  },
  mounted() {},
  methods: {},
};
</script>

<style scoped>
div.main_container {
  background-color: rgba(250, 238, 219, 0.945);
  display: flex;
  justify-content: center;
  margin: 10px;
  padding: 20px;
  border-radius: 10px;
}
.main_table {
  table-layout: fixed;
  width: 100%;
  height: 100%;
  border-collapse: collapse;
}
th {
  border-bottom: cornsilk 1.5px solid;
}
::v-deep .el-card {
  border: 0;
}
</style>
