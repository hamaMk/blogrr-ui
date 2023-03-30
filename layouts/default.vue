<template>
  <v-app>
    <v-layout>
      <!-- Header -->
      <v-app-bar
          color="teal-darken-4"
          image="https://picsum.photos/1920/1080?random"
      >
        <template v-slot:image>
          <v-img
              gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
          ></v-img>
        </template>

        <v-app-bar-title style="cursor: pointer" @click="$router.push('/')">Blogrr</v-app-bar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-account</v-icon>
        </v-btn>
      </v-app-bar>

      <!-- Content -->
      <v-main>
        <slot/>
      </v-main>

      <!-- Footer -->
    </v-layout>
    <footer class="px-10 py-5 text-center bg-black" >
      {{ new Date().getFullYear() }} — <strong>Blogrr</strong>
    </footer>
  </v-app>

</template>