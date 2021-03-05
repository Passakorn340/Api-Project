<template>
  <div id="app">
    <b-navbar type="warning" variant="warning">
      <b-navbar-nav>
        <router-link to="/" class="container">
          <b-iconstack font-scale="3" class="mr-3">
            <b-icon stacked icon="play-btn" variant="dark"></b-icon>
          </b-iconstack>
          <router-link to="/" id="name">Anime</router-link>
        </router-link>
      </b-navbar-nav>
      <b-navber-nav class="ml-auto">
        <b-nav-form>
          <b-form-input
            size="sm"
            class="mr-3"
            placeholder="Search"
            v-model="sh"
          ></b-form-input>
          <b-button size="sm" type="submit" @click="search"> Search </b-button>
        </b-nav-form>
      </b-navber-nav>
    </b-navbar>
    <router-view />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      sh: "",
      animeList: "",
      url: `https://api.jikan.moe/v3/producer/1/2`,
    };
  },
  methods: {
    search() {
      const router = this.$router;
      for (let i = 0; i <= this.animeList.anime.length; i++) {
        if (this.sh == this.animeList.anime[i].title) {
          alert(this.animeList.anime[i].title);
          router.push({
            path: `/toon/${this.animeList.anime[i].mal_id}`,
          });
          break;
        } else if (99 == i) {
          alert("Not listed!!!");
          router.push({
            path: `/`,
          });
        }
      }
    },
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.animeList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}

#name {
  color: #000000;
  font-size: 30px;
}
</style>
