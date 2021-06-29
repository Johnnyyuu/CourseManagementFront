<!-- created by Johnny in 2021/6/28 -->

<template>
  <!-- eslint-disable -->
  <div class="main_container">
    <!-- unfinished -->
    <el-row
      ><img
        src="./ut events.png"
        style="
          width: 100%;
          height: auto;
          border-radius: 8px;
          margin: 10px 0px;
          cursor: pointer;
        "
    /></el-row>
    <el-row>
      <el-row style="font-size: 14px; margin-bottom: 5px">Juen 26, 2021</el-row>
      <el-row
        ><a
          href="https://harthouse.ca/events/u-of-t-black-graduation-ceremony/"
          style="font-size: 20px"
          >U of T Black Graduation Ceremony</a
        >
      </el-row>
      <el-divider></el-divider>
      <el-row style="font-size: 14px; margin-bottom: 5px">Juen 28, 2021</el-row>
      <el-row
        ><a
          href="https://clnx.utoronto.ca/home/slevents.htm?eventId=31613"
          style="font-size: 20px"
          >Know Your Employment Rights</a
        >
      </el-row>
      <el-divider></el-divider>
      <a href="https://www.utoronto.ca/events">
        <el-button type="primary" size="small" style="margin-bottom: 10px"
          >More Info</el-button
        >
      </a>
    </el-row>
  </div>
</template>

<script>
import CourseCard from "./courseCard.vue";
export default {
  name: "KeySession",
  props: {},
  components: {},
  data() {
    return {};
  },

  created() {},
  mounted() {},
  methods: {},
};
</script>

<style scoped>
a {
  color: cornflowerblue;
}
a:hover {
  color: darkblue;
}
div.main_container {
  margin: 0px 20px;
}
::v-deep .el-divider--horizontal {
  margin: 20px 0px;
}
::v-deep .el-card {
  border: 0;
}
</style>
