<template>
  <div class="posts__wrapper">
    <PostCreate @addPost="addPost" />
    <div class="posts__list">
      <PostList :posts="posts" />
    </div>
  </div>
</template>
<script>
import PostCreate from "@/components/PostCreate.vue";
import PostList from "@/components/PostsList.vue";

export default {
  // name: "",
  data() {
    return {
      title: "",
      text: "",
      posts: [{ id: 1, title: "title1", text: "text" }],
    };
  },
  components: {
    PostCreate,
    PostList,
  },
  methods: {
    addPost(post) {
      // console.log(post);
      this.posts.push(post)
    },
  },
};
</script>

<style lang="scss">
body {
  background-color: #4c4c4c;
  color: #fff;
}
.posts {
  &__wrapper {
    max-width: 700px;
    margin: auto;
  }
  &__form {
    border: 1px solid #fff;
    padding: 20px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    margin-bottom: 30px;
    input {
      margin-bottom: 10px;
      padding: 10px 20px;
      border-radius: 5px;
      border: none;
    }
    button {
      background-color: #131313;
      border: none;
      color: #fff;
      border-radius: 5px;

      padding: 15px;
      cursor: pointer;
    }
  }
  &__item {
    display: flex;
    flex-direction: column;
    border-radius: 10px;
    border: 1px solid #fff;
    padding: 20px;
    margin-bottom: 20px;
  }
}
</style>
