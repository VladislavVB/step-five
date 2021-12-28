<template>
  <form class="posts__form" @submit.prevent>
    <input placeholder="Название" v-model="post.title" type="text" />
    <input placeholder="Текст" v-model="post.text" type="text" />
    <button @click="addPost()">Запостить</button>
  </form>
</template>
<script>
export default {
  data() {
    return {
      post: {
        title: "",
        text: "",
      },
    };
  },
  methods: {
    addPost() {
      this.post.id = Date.now();
      this.$emit("addPost", this.post);
      this.post = {
        title: "",
        text: "",
      };
    },
  },
};
</script>

<style lang="scss"></style>
