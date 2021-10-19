<template>
  <div class="blog-page-wrapper">
    <div class="page-title-wrapper">
      <!-- <img :src="'http://localhost:1337' + blogData.thumbnail[0].url" alt="" /> -->
      <h1 class="page-title">{{ blogData.title }}</h1>
    </div>
    <div class="page-content-wrapper">
      <p>{{ blogData.blogDescription }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blogData: []
    };
  },
  methods: {
    async getBlogsList() {
      const blogsList = await this.$axios
        .get("http://localhost:1337/blogs/" + this.$route.params.index)
        .then(res => res.data);
      console.log(this.blogData);
      this.blogData = blogsList;
    }
  },
  mounted() {
    this.getBlogsList();
  }
};
</script>

<style>
.blog-page-wrapper {
  background-color: #ffffff;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.16);
  padding: 4% 4% 1%;
  box-sizing: border-box;
  margin: 4vh auto 0;
  width: 70vw;
}
.page-content-wrapper > p {
  line-height: 1.2em;
}
</style>
