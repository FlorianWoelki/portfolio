<template>
  <div
    class="container h-screen max-w-4xl px-8 pt-8 pb-32 mx-auto break-words lg:pt-16 md:px-16"
  >
    <h1 class="inline-block text-3xl border-b dark:text-gray-300">
      List 100 - Bucket List
    </h1>
    <p class="mt-4 dark:text-gray-400">
      Things I want to do before I die. <i>(Progress as of April 30, 2021)</i>
    </p>
    <div
      class="grid grid-cols-1 mt-6 space-y-2 sm:gap-4 sm:grid-cols-3 sm:space-y-0"
    >
      <div
        v-for="columnIndex in 3"
        :key="columnIndex"
        class="space-y-2 dark:text-gray-400"
      >
        <p
          v-for="(bucket, index) in list100Data.slice(
            (columnIndex - 1) * Math.ceil(list100Data.length / 3),
            Math.ceil(list100Data.length / 3) * columnIndex,
          )"
          :key="bucket.name"
          class="space-x-2 text-base"
        >
          <span
            class="font-bold text-red-500"
            :class="{ 'text-blue-500': bucket.done }"
          >
            {{
              index +
              1 -
              Math.ceil(list100Data.length / 3) +
              Math.ceil(list100Data.length / 3) * columnIndex
            }}
          </span>
          <del v-if="bucket.done">{{ bucket.name }}</del>
          <span v-else>
            {{ bucket.name }}
          </span>
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import list100Data from '@/assets/list100.json';

export default defineComponent({
  setup() {
    return {
      list100Data,
    };
  },
});
</script>
