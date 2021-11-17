<template>
  <div class="courses">
    <div v-for="course in courses" v-bind:key="course.id">
      {{ course.title }}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      courses: [],
    };
  },
  created() {
    axios.get("http://localhost:1337/courses").then((response) => {
      console.log(response);
      this.courses = response.data;
    });
  },
  methods: {},
};
</script>
