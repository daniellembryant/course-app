<template>
  <div id="app">
    <div v-for="course in courses" v-bind:key="course.id">
      <div>
        <b-card
          :title="course.title"
          :img-src="`http://localhost:1337${course.image.url}`"
          :img-alt="course.title"
          img-top
          tag="article"
          style="max-width: 20rem"
          class="mb-2"
        >
          <b-card-text>
            {{ course.description }}
          </b-card-text>

          <b-button href="#" variant="primary">Purchase for ${{ course.price }}</b-button>
        </b-card>
      </div>
    </div>
  </div>
</template>

<style></style>

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
      console.log(response.data);
      this.courses = response.data;
    });
  },
  methods: {},
};
</script>
