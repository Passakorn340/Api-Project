<template>
  <div class="container mt-5">
    <b-row>
      <b-col class="col-5">
        <b-img :src="toonList.image_url" style="height: 35rem; width: 25rem">
        </b-img>
      </b-col>
      <b-col class="col-6 bg-info">
        <b-row class="mt-3 container">
          <h2><strong>{{ toonList.title }}</strong></h2>
        </b-row>
        <b-row class="mt-3 container">
          <h4>English : {{ toonList.title_english }}</h4>
        </b-row>
        <b-row class="mt-3 container">
          <h4>Japanese : {{ toonList.title_japanese }}</h4>
        </b-row>
        <b-row class="mt-3 container">
          <h4>Duration : {{ toonList.duration }}</h4>
        </b-row>
        <b-row class="mt-3 container">
          <h4>Synopsis : </h4>{{ toonList.synopsis }}
        </b-row>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      toonList: "",
      url: `https://api.jikan.moe/v3/anime/${this.$route.params.id}`,
    };
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.toonList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
