<template>
  <div class="posts__wrapper">
    <PostCreate @addPost="addPost" />
    <div class="posts__list">
      <PostList :posts="posts" @remove="removePost" @star="starPost" />
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
      posts: [],
    };
  },
  components: {
    PostCreate,
    PostList,
  },
  mounted() {
    console.log(localStorage);
    // localStorage.clear()
    console.log(JSON.parse(localStorage.getItem("post")));
    this.posts = JSON.parse(localStorage.getItem("post"));
    console.log(this.posts);
  },
  methods: {
    addPost(post) {
      // console.log(post);
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
      console.log(JSON.parse(localStorage.getItem("post")));
    },
    starPost(post) {
      console.log(post);
      localStorage.setItem("post", JSON.stringify(post));
      console.log(localStorage);
      // localStorage.getItem("post");
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
    &-head {
      display: flex;
    }
  }
}
</style>
