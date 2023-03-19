        <script>
import { store } from "../store";
import axios from "axios";

export default {
  name: "SinglePost",
  data() {
    return {
      store,
      post: null,
      loading: true,
    };
  },
  mounted() {
    this.loading = true;
    axios
      .get(`${this.store.baseUrl}/api/posts/${this.$forceUpdate.params.slug}`)
      .then((response) => {
        this.post = response.data.post;
        this.loading = false;
      });
  },
};
</script>

<template lang="">
    <div class="container">
        <div class="row">
            <div v-if="loading">
            <div class="loader"></div>
        </div>
            <div v-else class="col-12">
        <h2>{{post.title}}</h2> 
        <div class="cover_img">
            <img :src="`${this.store.baseUrl}/storage/${post.cover_image}`" class="img-fluid">
        </div>
    </div>
  </div>
      
    </div>
</template>

<style lang="">
</style>
