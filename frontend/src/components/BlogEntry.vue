<script setup lang="ts">

import { Blog } from '../types/Blog'

defineProps<{
  blog: Blog
}>();

</script>

<template>

  <v-card
      class="mx-auto"
      max-width="450"
    >
    <v-img
      :src="blog?.pictures[0]?.content || 'https://cdn.vuetifyjs.com/images/parallax/material.jpg'"
      cover
      :aspect-ratio="16/9"
    >
    </v-img>
    <v-card-title class="flex-column align-start">
      <div class="text-h4 mb-2">
         {{ blog.title }}
      </div>
      <div class="text-h6 font-weight-regular text-grey">
        {{ blog.content }}
      </div>
      <div class="d-flex align-center">
        <!-- Task -->
        <!-- <v-avatar
          size="24"
          class="me-4"
        >
          <v-img
            :src="imageUrl"
            contain
          ></v-img>
        </v-avatar> -->

        <!-- <span class="text-body-2 text-grey">81° / 62°</span> -->
      </div>
    </v-card-title>

    <v-divider class="mx-4"></v-divider>

    <v-card-text class="d-flex">
      <v-icon icon="mdi-heart" v-if="blog.isLiked" @click="$emit('triggerLike')"></v-icon>
      <v-icon icon="mdi-heart-outline" v-else @click="$emit('triggerLike')"></v-icon>
      <v-icon icon="mdi-checkerboard" class="ml-2"  @click="$emit('turnGrayscale')"></v-icon>
      <v-icon icon="mdi-delete" class="ml-auto"  @click="$emit('deletePost', $event, blog.id)"></v-icon>
    </v-card-text>
  </v-card>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
