<script setup lang="ts"></script>

<template>
  <div>
    <!-- Blog List  -->
    <ContentList
      path="/posts"
      fields="title,date,thumbnail"
      :query="{
        draft: false,
        sort: [
          {
            date: -1,
          },
        ],
      }"
      v-slot="{ list }"
    >

      <div
        v-for="blog in list"
        :key="blog._path"
        class="blog-card bg-white rounded-2xl overflow-hidden mb-4"
      >
        <!-- Image -->
        <div class="h-[300px] relative">
          <img
            v-if="blog.thumbnail"
            :src="blog.thumbnail"
            :alt="blog.title"
            class="absolute w-full h-full object-cover"
          />
        </div>

        <div class="blog-card--meta my-4 ml-4">
          <!-- title -->
          <h3 class="text-2xl font-bold">
            <NuxtLink :to="blog.slug">{{ blog.title }}</NuxtLink>
          </h3>
          <!-- date -->
          <div class="text-sm text-gray-500 mt-px block">{{ blog.date }}</div>
          <!-- tags -->
          <div v-if="blog.tags" class="mt-2 text-xs">
            <span v-for="tag in blog.tags" class="p-1 rounded bg-gray-100 mr-2">
              {{ tag }}</span
            >
          </div>
          
        </div>
      </div>
    </ContentList>
  </div>
</template>
