<template>
  <div v-for="post in posts" :key="post.id" class="posts__item">
    <div class="posts__item-head">
      <button @click="$emit('remove', post)"> Удалить</button>
      <button @click="$emit('star', post)">В избранное</button>
    </div>
    {{ post.title }}
    {{ post.text }}
  </div>
</template>
<script>
export default {
  props: {
    posts: {
      type: Array,
    },
  },
  methods: {
    // deleteCard() {
    //   this.$emit("deleteCard", this.post)
    // },
  },
};
</script>

<style lang="scss"></style>
