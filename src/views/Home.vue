<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <card
        v-for="item in List.anime"
        :key="item"
        :id="item.mal_id"
        :Image="item.image_url"
        :Title="item.title"
      />
    </div>
  </div>
</template>

<script>
import card from "@/components/HelloWorld.vue";
import axios from "axios";

export default {
  components: {
    card,
  },
  data() {
    return {
      List: "",
      url:
        "https://api.jikan.moe/v3/producer/1/2",
    };
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.List = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
