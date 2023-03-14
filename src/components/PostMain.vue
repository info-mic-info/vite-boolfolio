        <script>
export default {
  name: "PostMain",
  data() {
    return {
      posts: [],
      loading: true,
      baseUrl: "http://127.0.0.1:8000",
    };
  },
  methods: {
    getPosts() {
      this.loading = true;
      axios.get(`${this.baseUrl}/api/posts`).then((response) => {
        this.post = response.data.results;
        this.loading = false;
      });
    },
  },
};
</script>

<template lang="">
    <div>
        
    </div>
</template>


<style lang="scss" scoped>
</style>