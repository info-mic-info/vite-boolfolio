<script>
import axios from "axios";

import { store } from "../store";

import PostCard from "../components/PostCard.vue";

export default {
  name: "PostList",
  data() {
    return {
      store,
      posts: [],
      currentPage: 1,
      lastPage: null,
      loading: true,
    };
  },

  components: {
    PostCard,
  },

  methods: {
    getPosts(post_page) {
      this.loading = true;
      axios
        .get(`${this.store.baseUrl}/api/stores`, {
          params: { page: store_page },
        })
        .then((response) => {
          // this.posts = response.data.results.data;

          this.posts = response.data.results.data;
          this.currentPage = response.data.results.data.current_page;
          this.lastPage = response.data.results.data.last_page;
          this.loading = false;
        });
    },
  },
  mounted() {
    this.getPosts(this.currentPage);
  },
};
</script>

<template lang="">
    <div>
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <h2 class="text-center">Vite-Boolfolio</h2>
                </div>
                <div class="col-12">
                   <div v-if="loading" class="col-12 justify-content-center">
                    <div class="loader"></div>
                </div>
                <div v-else class="d-flex justify-content-center flex-wrap">
                    <div class="card" v-for="post in posts" :key="post.id">
                        <PostCard :post="post"/>
                    </div>
                    <div class="row">
                        <div class="col-12">
                            <nav>
                                <ul class="pagination">


                                    <li :class="currentPage === 1 ? 'disabled' : 'page-item'">
                                        <button class="page-link"
                                        @click="getPosts(currentPage - 1)">Prev</button>
                                    </li>


                                    <li :class="currentPage === i ? 'disabled' : 'page-item'" v-for="i in lastPage" >
                                        <button class="page-link" @click="getPosts(i)">{{i}}</button>
                                    </li>

                                    <li :class="currentPage === lastPage ? 'disabled' : 'page-item'">
                                        <button class="page-link" 
                                        @click="getPosts(currentPage + 1)">Next</button>
                                    </li>


                                </ul>
                            </nav>
                        </div>
                    </div>
                </div>
                </div>
                
            </div>
        </div>
    </div>
</template>


<style lang="scss" scoped>
</style>