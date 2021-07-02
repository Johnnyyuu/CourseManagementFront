<!-- created by Johnny in 2021/6/16 -->
<template>
  <!-- eslint-disable -->
  <div class="main">
    <el-card>
      <el-row>
        <span class="title"><i class="fa fa-book fa-fw"></i> Course List </span>
        <el-button
          type="primary"
          style="float: right; margin-bottom: 10px"
          @click="showAdd()"
          >Add Course</el-button
        >
      </el-row>
      <el-table :data="courseList" stripe style="width: 100%">
        <el-table-column fixed prop="name" label="Code" width="100">
        </el-table-column>
        <el-table-column fixed prop="fullName" label="Name" width="180">
        </el-table-column>
        <el-table-column fixed prop="teacher" label="Teacher" width="180">
        </el-table-column>
        <el-table-column fixed prop="location" label="Location" width="180">
        </el-table-column>
        <el-table-column fixed prop="emphasis" label="Emphasis" width="180">
          <template slot-scope="scope">
            <el-tag
              v-for="(item, key) in scope.row.emphasis"
              style="margin: 2px 0px 2px 0px"
            >
              {{ item }}
            </el-tag>
          </template>
        </el-table-column>
        <el-table-column fixed prop="option" label="Options" width="200">
          <template slot-scope="scope">
            <el-button
              @click.native.prevent="deleteRow(scope)"
              size="small"
              type="primary"
            >
              Edit
            </el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-card>
    <el-dialog class="dialog" title="Course Info" :visible.sync="showadd">
      <el-form :model="addForm">
        <el-form-item label="Code">
          <el-input v-model="addForm.name" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Name">
          <el-input v-model="addForm.fullName" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Teacher">
          <el-input v-model="addForm.teacher" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Location">
          <el-input v-model="addForm.location" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Emphasis">
          <el-input v-model="addForm.emphasis" autocomplete="off"></el-input>
        </el-form-item>
        <!-- <el-form-item label="活动区域" :label-width="formLabelWidth">
          <el-select v-model="form.region" placeholder="请选择活动区域">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item> -->
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="cancelAdd()">取 消</el-button>
        <el-button type="primary" @click="addCourse()">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
import "@/styles/main-container.scss";
// import { getList } from "@/api/table";
// import TimeTable from "../dashboard/components/timeTable";
// import CourseSelector from "./components/courseSelector";
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
      showadd: false,
      addForm: {
        name: "",
        fullName: "",
        teacher: "",
        location: "",
        time: [],
        tech: true,
        emphasis: "",
      },
      // todo:
      courseList: [
        {
          _id: null,
          name: "ECE1762",
          fullName: "Algorithms and Data Structure",
          teacher: "Zissis Poulos",
          location: "BA207",
          time: [
            [0, 0, 0, 0, 0, 0, 0],
            [0, 1, 0, 0, 0, 0, 0],
            [0, 0, 0, 0, 0, 0, 0],
            [0, 1, 0, 0, 0, 0, 0],
            [0, 1, 0, 0, 0, 0, 0],
          ],
          tech: true,
          emphasis: ["Computer Engineering", "Statistics"],
        },
      ],
    };
  },
  components: {
    // TimeTable,
    // CourseSelector,
  },
  created() {
    this.fetchData();
  },
  methods: {
    // add new course to system
    addCourse() {
      this.showadd = false;
      this.$http.post("addCourse", this.addForm).then((response) => {
        this.$message({
          message: "Add successful",
          type: "success",
        });
        this.fetchData();
      });
    },
    showAdd() {
      this.showadd = true;
    },
    cancelAdd() {
      this.showadd = false;
      this.addForm = {
        name: "",
        fullName: "",
        teacher: "",
        location: "",
        time: [],
        tech: true,
        emphasis: "",
      };
    },

    // load course list
    fetchData() {
      this.$http.get("courseList").then((response) => {
        // console.log(response);
        this.courseList = response.data;
      });
    },

    deleteRow(index, rows) {
      rows.splice(index, 1);
    },
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
.title {
  font-size: 25px;
  line-height: 40px;
  color: rgb(68, 68, 160);
}
.dialog {
}
::v-deep .el-dialog {
  border-radius: 8px;
}
</style>
