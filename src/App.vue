<template>
  <div class="posts__wrapper">
    <form class="posts__form" @submit.prevent>
      <input placeholder="Название" v-model="title" type="text" >
      <input placeholder="Текст" v-model="text" type="text" >
      <button v-if="this.text.lenth > 1" @click="addPost()" >Запостить</button>
    </form>
    <div class="posts__list">
      <div v-for="post in posts" :key="post" class="posts__item">
        {{ post.title }}
        {{ post.text }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "",
  data() {
    return {
      title: '',
      text: '',
      posts: [
        { id: 1, title: "title1", text: "text" },
      ],
    };
  },
  methods: {
    addPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        text: this.text,
      }
      this.posts.push(newPost);
      this.title = '';
      this.text = '';
    }
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
