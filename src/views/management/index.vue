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
      <el-row style="margin: 10px 5px"
        ><span>Search a Course: </span
        ><el-input
          v-model="searchInput"
          placeholder="Input course name or code"
          style="width: 30%"
        ></el-input
      ></el-row>
      <el-table :data="cur_list" stripe style="width: 100%">
        <el-table-column fixed prop="name" label="Code"> </el-table-column>
        <el-table-column fixed prop="fullName" label="Name"> </el-table-column>
        <el-table-column fixed prop="teacher" label="Teacher">
        </el-table-column>
        <el-table-column fixed prop="location" label="Location">
        </el-table-column>
        <el-table-column fixed prop="emphasis" label="Emphasis">
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
              type="primary"
              icon="el-icon-edit"
              circle
              @click.native.prevent="showEdit(scope.row)"
            ></el-button>
            <el-button
              type="danger"
              icon="el-icon-delete"
              circle
              @click.native.prevent="deleteCourse(scope.row)"
            >
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
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="cancelAdd()">取 消</el-button>
        <el-button type="primary" @click="addCourse()">确 定</el-button>
      </div>
    </el-dialog>

    <el-dialog class="dialog" title="Course Info" :visible.sync="showedit">
      <el-form :model="editForm">
        <el-form-item label="Code">
          <el-input
            v-model="editForm.name"
            autocomplete="off"
            disabled
          ></el-input>
        </el-form-item>
        <el-form-item label="Name">
          <el-input v-model="editForm.fullName" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Teacher">
          <el-input v-model="editForm.teacher" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Location">
          <el-input v-model="editForm.location" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Emphasis">
          <el-input v-model="editForm.emphasis" autocomplete="off"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="cancelEdit()">取 消</el-button>
        <el-button type="primary" @click="editCourse(editForm.id)"
          >确 定</el-button
        >
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
  data() {
    return {
      searchInput: "",
      showedit: false,
      showadd: false,
      editForm: {
        name: "",
        fullName: "",
        teacher: "",
        location: "",
        time: [],
        tech: true,
        emphasis: null,
        id: null,
      },
      addForm: {
        name: "",
        fullName: "",
        teacher: "",
        location: "",
        time: [],
        tech: true,
        emphasis: null,
      },
      // addForm: {},
      // todo:
      courseList: [],
      cur_list: [],
    };
  },
  watch: {
    searchInput: function (value) {
      this.debounce(this.filterCourse(value), 500);
    },
  },
  components: {
    // TimeTable,
    // CourseSelector,
  },
  created() {
    this.fetchData();
  },
  methods: {
    // load course list
    fetchData() {
      this.$http.get("courseList").then((response) => {
        // console.log(response);
        this.courseList = response.data;
        this.cur_list = this.courseList;
      });
    },

    // add new course to system
    addCourse() {
      this.showadd = false;
      this.$http.post("addCourse", this.addForm).then((response) => {
        if (response.data.status === 200) {
          this.$message({
            message: response.data.message,
            type: "success",
          });
          this.fetchData();
        } else if (response.data.status === 400) {
          this.$message({
            message: response.data.message,
            type: "warning",
          });
        } else {
          this.$message({
            message: response.data.message,
            type: "error",
          });
        }
      });
      this.addForm = {
        name: "",
        fullName: "",
        teacher: "",
        location: "",
        time: [],
        tech: true,
        emphasis: null,
      };
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
        emphasis: null,
      };
    },

    //edit course info
    editCourse(id) {
      let cur_id = id;
      this.$http
        .post(`editCourse/${cur_id}`, this.editForm)
        .then((response) => {
          if (response.data.status === 200) {
            this.$message({
              message: response.data.message,
              type: "success",
            });
            this.fetchData();
          } else {
            this.$message({
              message: response.data.message,
              type: "warning",
            });
          }
        });
      this.showedit = false;
    },
    showEdit(row) {
      this.editForm.name = row.name;
      this.editForm.fullName = row.fullName;
      this.editForm.teacher = row.teacher;
      this.editForm.location = row.location;
      this.editForm.id = row._id;
      this.showedit = true;
      //todo:emphasis
      this.editForm.emphasis = row.emphasis;
    },
    cancelEdit() {
      this.showEdit = false;
      this.editForm = {};
    },

    // Delete Course
    deleteCourse(id) {
      let cur_id = id;
      this.$http.delete(`deleteCourse/${cur_id}`).then((response) => {
        if (response.data.status === 200) {
          this.$message({
            message: response.data.message,
            type: "success",
          });
          this.fetchData();
        }
      });
    },

    // Search Course
    filterCourse(value) {
      this.cur_list = this.courseList.filter((course) => {
        return (
          course.name.indexOf(value) !== -1 ||
          course.fullName.indexOf(value) !== -1
        );
      });
    },
    debounce(func, delay) {
      let timer = null;
      return function () {
        clearTimeout(timer);
        setTimeout(() => {
          func.apply(this);
        }, delay);
      };
    },
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
