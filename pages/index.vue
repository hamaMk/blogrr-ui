<template>
  <v-container class="mt-10">
    <div>
      <v-text-field
          v-model="searchQuery"
          @keyup="searchPosts"
          prepend-inner-icon="mdi-magnify"
          density="compact"
          placeholder="Search for posts"
          clearable
          variant="solo"
      ></v-text-field>
    </div>

    <v-row>
      <v-col cols="12" xl="8" lg="8" md="8" sm="8">
      <div class="">
        <div v-for="post in posts">
            <BlogPost :post="post"/>
        </div>
      </div>
      </v-col>
      <v-col cols="12" xl="4" lg="4" md="4" sm="4">
       <v-card class="text-center" title="Popular Tags">
         <div class="d-flex flex-wrap">
            <div v-for="tag in tags">
              <NuxtLink to="/" style="text-decoration: none; cursor: pointer">
                  <v-chip
                  class="ma-2"
                  color="teal"
                >
                  {{ tag.name }}
                </v-chip>
              </NuxtLink>
           </div>
         </div>
       </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import BlogPost from "../components/BlogPost";
import {refreshNuxtData, useFetch} from "nuxt/app";
import {ref} from "vue"

const searchQuery = ref("")


const { data: posts, pending, error, refresh } = await useFetch('http://127.0.0.1:8000/api/posts/', {
  query: { search: searchQuery }
})
const { data: tags } = await useFetch('http://127.0.0.1:8000/api/tags/')
function searchPosts(){
  refresh()
}
</script>

<style scoped>

</style>