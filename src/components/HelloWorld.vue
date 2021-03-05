<template>
  <div>
    <b-card
      :title="Title"
      :img-src="Image"
      img-alt="Image"
      img-left
      tag="article"
      style="height: 17rem; width: 30rem"
      class="mb-3 mr-3"
    >
      <router-link :to="`/toon/${this.id}`">
        <b-button variant="success">See more</b-button>
      </router-link>
    </b-card>
  </div>
</template>

<script>
export default {
  props: {
    id: Number,
    Image: String,
    Title: String,
  },
};
</script>

<style></style>
