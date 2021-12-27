<template>
  <div v-for="post in posts" :key="post" class="posts__item">
    {{ post.title }}
    {{ post.text }}
  </div>
</template>
<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    }
  }
};
</script>

<style lang="scss"></style>
