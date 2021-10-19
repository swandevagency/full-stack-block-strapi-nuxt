<template>
  <div class="home-page-wrapper">
    <div class="page-title-wrapper">
      <h1 class="page-title">Welcome</h1>
    </div>
    <div class="page-content-wrapper">
      <BlogItem
        :blogTitle="blogItem.title"
        :blogDescription="blogItem.blogDescription"
        :blogThumbnail="'http://localhost:1337' + blogItem.thumbnail[0].url"
        :index="blogItem.id"
        v-for="(blogItem, index) in blogsList"
        :key="index"
      />
    </div>
  </div>
</template>

<script>
import BlogItem from "../../components/blogItem.vue";
export default {
  data() {
    return {
      blogsList: []
    };
  },
  components: {
    BlogItem
  },
  methods: {
    async getBlogsList() {
      const blogsList = await this.$axios
        .get("http://localhost:1337/blogs")
        .then(res => res.data);
      this.blogsList = blogsList;
    }
  },
  mounted() {
    this.getBlogsList();
    setTimeout(() => {
      console.log(this.blogsList);
    }, 1000);
  }
};
</script>

<style>
.home-page-wrapper {
  background-color: #ffffff;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.16);
  padding: 4% 4% 1%;
  box-sizing: border-box;
  margin: 4vh auto 0;
  width: 70vw;
}
</style>
