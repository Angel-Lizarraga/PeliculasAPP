<template>
  <v-app>
    <!-- App bar -->
    <v-app-bar :elevation="2">
      <template v-slot:prepend>
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      </template>
      <v-app-bar-title>PelículasAPP</v-app-bar-title>
    </v-app-bar>

    <!-- Navigation drawer -->
    <v-navigation-drawer v-model="drawer" app>
      <v-list-item title="PeliculasAPP" subtitle="" ></v-list-item>
      <v-divider></v-divider>
      <v-list-item to = '/' link title="Home"></v-list-item>
      <v-list-item to = '/pagina2' link title="Página 2"></v-list-item>
      <v-list-item to = '/table' link title="Tabla Películas"></v-list-item>
    </v-navigation-drawer>

    <!-- Main content -->
    <v-main>
      <router-view />
    </v-main>

    <!-- Footer -->
    <AppFooter />
  </v-app>
</template>

<script setup>
import { ref } from 'vue'

const drawer = ref(false)
</script>