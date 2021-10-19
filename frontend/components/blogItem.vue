<template>
  <div class="blog-item-wrapper">
    <div class="blog-thumbnail">
      <img :src="blogThumbnail" alt="" />
    </div>
    <div class="blog-preview">
      <div class="blog-title">
        <h2>{{ blogTitle }}</h2>
      </div>
      <div class="blog-description">
        <p>{{ blogDescription.substring(0, 200) + "..." }}</p>
        <nuxt-link :to="'/homepage/' + index" ref="readMore"
          >Read more</nuxt-link
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    blogTitle: String,
    blogDescription: String,
    blogThumbnail: String,
    index: Number
  }
};
</script>

<style>
.blog-item-wrapper {
  user-select: none;
  overflow: hidden;
  transition: transform 0.3s, background-color 0.3s, box-shadow 0.3s;
  display: flex;
  cursor: pointer;
  border-radius: 3px;
  background-color: #f1f1f1;
  border: 1px solid rgba(0, 0, 0, 0.16);
  color: #111111;
  margin-bottom: 1em;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}
.blog-item-wrapper:hover {
  background-color: #fafafa;
  box-shadow: 0 3px 36px rgba(0, 0, 0, 0.16);
  transform: scale(1.03);
}
.blog-thumbnail {
  flex-basis: 30%;
  min-width: 180px;
  max-height: 200px;
}
.blog-thumbnail > img {
  width: 100%;
  object-fit: cover;
  height: 100%;
}
.blog-preview {
  padding: 1em 2em;
}
.blog-title > h2 {
  margin-bottom: 1em;
  font-weight: 500;
}
.blog-description > p {
  margin-bottom: 1em;
  line-height: 1.2em;
}
.blog-description > a {
  text-decoration: none;
  color: var(--theme-color);
}
</style>
