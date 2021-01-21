<template>
  <div class="flex flex-col h-full">
    <div class="relative flex flex-1 flex-col space-y-2 px-6 py-8 group">
      <a
        :href="module.website"
        :aria-label="module.website"
        target="_blank"
        rel="noopener"
        class="absolute inset-0"
      />

      <nuxt-image
        :src="iconUrl(module)"
        :alt="module.name"
        width="40px"
        height="40px"
      />

      <h2 class="flex text-2xl items-center pt-2">
        <span>{{ module.name }}</span>
        <img
          v-if="module.type === 'popular'"
          alt="popular"
          src="~/assets/icons/official.svg"
          width="20"
          height="20"
          class="ml-1 mt-1"
        />
      </h2>
      <p class="text-gray-500 group-hover:text-gray-800">
        {{ module.description }}
      </p>
    </div>
    <div class="border-t border-gray-200 bg-gray-100 grid grid-cols-3">
      <p
        class="stats-block group flex items-center space-x-1 py-3 px-4 border-r border-gray-200 hover:bg-gray-200 hover:bg-opacity-50"
      >
        {{ module.category }}
      </p>

      <div
        class="stats-block group flex items-center space-x-1 py-3 px-4 z-0 overflow-hidden hover:bg-gray-200 hover:bg-opacity-50"
      >
        <p>view</p>
      </div>
    </div>
  </div>
</template>

<script>
import { numberFormatter } from "~/utils/format.ts";

export default {
  name: "CardModule",
  props: {
    module: {
      type: Object,
      required: true,
    },
  },
  methods: {
    numberFormat(num, options = { precision: 1 }) {
      return numberFormatter(num, options);
    },
    iconUrl({ icon, category }) {
      if (icon) {
        return `/icons/${icon}`;
      }
      return `/categories/${category.toLowerCase()}.svg`;
    },
    npmUrl({ npm }) {
      return `https://npmjs.com/package/${npm}`;
    },
    githubUrl({ github }) {
      return `https://github.com/${github}`;
    },
  },
};
</script>

<style scoped>
.stats-block {
  & img {
    filter: grayscale(100%);
    &.icon {
      filter: grayscale(100%) contrast(0%);
    }
  }
  &:hover {
    & img {
      filter: none;
      &.icon {
        filter: none;
      }
    }
  }
}
</style>
