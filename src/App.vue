\<template>
  <v-app>
    <!-- MENU BAR DI ATAS -->
    <v-app-bar app color="primary" dark>
      <v-app-bar-title> Form Data Siswa</v-app-bar-title>
    </v-app-bar>

    <!-- KONTEN UTAMA -->
    <v-main>
      <FormSiswa />
    </v-main>
  </v-app>
</template>

<script setup>
import FormSiswa from './components/FormSiswa.vue'
</script>
