<template>
  <v-app-bar color="surface-variant" :title="title"></v-app-bar>
</template>

<script setup>
const { title } = defineProps(["title"]);
</script>

<style scoped></style>
