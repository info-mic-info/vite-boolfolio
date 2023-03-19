        <script>
import { store } from "../store.js";

export default {
  name: "PostCard",
  props: {
    post: Object,
  },
  data() {
    return {
      store,
    };
  },
};
</script>


<template lang="">
    <div class="card">
        <div class="card-body">
                            <div class="card-img-top">
                                <img class="img-fluid" :src="post.cover_image !=null ? `${baseUrl}/storage/${post.cover_image}` : 'nessuna immagine'">
                            </div>
                            <div class="card-title">
                                <h5>{{post.title}}</h5>
                                <em>Categoria: {{ post.type.name}}</em>
                                <em>Tags: <span v-for="tag in post.tags">
                                    {{ tag.name}}
                                </span>
                            </em>
                            </div> 
                            <div class="card-text">
                                {{post.excerpt}}
                            </div>
                            <!-- <a href="" class="btn">Leggi articolo</a>   -->
                            <router-link :to="{name: 'single-post', params: { slug: post.slug}}" class="btn" >Leggi L'articolo</router-link>
                        </div>
    </div>
</template>


<style lang="">
</style>