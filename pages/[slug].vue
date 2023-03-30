<template>
  <v-container>
    <v-row>
      <v-col cols="12" xl="8" lg="8" md="8" sm="8">
      <div class="">
        <h1>{{ post.title }}</h1>
        <hr>
        <div v-html="post.content" class="mt-10"></div>
      </div>
      </v-col>
      <v-col cols="12" xl="4" lg="4" md="4" sm="4">
       <v-card class="text-center" title="Other Posts">
         <div class="text-left px-5 py-2">
            <div v-for="post in posts.slice(0, 5)">
              <NuxtLink :to="`/${post.slug}`" style="text-decoration: none; cursor: pointer; color: teal">
                  {{ post.title }}
              </NuxtLink>
           </div>
         </div>
       </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import {useFetch, useRoute} from "nuxt/app";

const {slug} = useRoute().params
const { data: post } = await useFetch(`http://127.0.0.1:8000/api/posts/${slug}/`)
const { data: posts } = await useFetch('http://127.0.0.1:8000/api/posts/')
</script>

<style scoped>

</style>