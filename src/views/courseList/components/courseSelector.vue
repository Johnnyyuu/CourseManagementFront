<!-- created by Johnny in 2021/6/16 -->
<template>
  <div class="main"></div>
</template>

<script>
// import { getList } from "@/api/table";
export default {
  name: "CourseSelector",
  data() {
    return {
      // todo:
    };
  },
  components: {},
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
* {
  font-family: "Times New Roman", Times, serif;
}
</style>
