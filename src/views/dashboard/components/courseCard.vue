<!-- created by Johnny in 2021/6/16 -->
<!--  -->
<template>
  <div class="mainContainer">
    <el-card
      class="mainCard"
      @mouseover.native="handleHover"
      @mouseleave.native="handleLeave"
      v-if="CourseName !== ''"
      :class="CourseName"
    >
      <el-row
        ><span class="className">{{ CourseName }}</span></el-row
      >
      <div class="classInfo">
        <span style="display: block">{{ Location }}</span>
        <span style="display: block">{{ Teacher }}</span>
      </div>
    </el-card>
    <div class="mainCardhide" v-if="CourseName === ''"></div>
  </div>
</template>

<script>
export default {
  name: "CourseCard",
  data() {
    return {
      onHover: false,
    };
  },
  props: {
    CourseName: {
      type: String,
      default: "",
    },
    Color: {},
    Teacher: { type: String, default: "TBA" },
    Location: { type: String, default: "TBA" },
  },
  mounted() {
    if (this.CourseName !== "") {
      let target = document.getElementsByClassName(this.CourseName);
      for (let item of target) {
        this.giveColor(item);
      }
    }
  },
  methods: {
    giveColor(target) {
      if (this.Color === 1) {
        target.style.backgroundColor = "cornflowerblue";
      } else if (this.Color === 2) {
        target.style.backgroundColor = "burlywood";
      } else {
        target.style.backgroundColor = "yellowgreen";
      }
    },

    handleHover() {
      this.onHover = true;
    },

    handleLeave() {
      this.onHover = false;
    },
  },
};
</script>

<style>
.mainContainer {
  display: flex;
  justify-content: center;
  margin: 5px 10px 5px 10px;
}
.mainCard {
  height: 70px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
  cursor: pointer;
  color: black;
}
.mainCard:hover {
  transform: translateY(-3px) translateX(2px);
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
}
.mainCardhide {
  height: 60px;
  width: 100%;
}
.className {
  font-size: 110%;
  font-family: "Times New Roman", Times, serif;
}
.classInfo {
  font-size: 90%;
  font-family: "Times New Roman", Times, serif;
}
</style>