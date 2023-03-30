<template>
  <div class="pb-10">
    <h2>
      <NuxtLink :to="`/${post.slug}`" class="post-nav">{{ post.title }}</NuxtLink>
    </h2>
    <small class="label-light">
      {{ post.pub_date.substring(0, 10) }}
      <span v-if="post.owner">| {{ post.owner.firstname }} {{ post.owner.lastname }}</span>
    </small>
    <p>
      {{ post.short_description }}
      <br>
      <NuxtLink :to="`/${post.slug}`" class="post-link">Read more &rarr;</NuxtLink>
    </p>
  </div>
</template>

<script setup>
const props = defineProps(['post'])
</script>

<style scoped>
  .label-light{
    color: gray;
  }
  .post-nav{
    color: black;
    text-decoration: none;
  }
  .post-link{
    color: dodgerblue;
    font-size: 10px;
    text-decoration: none;
  }
</style>