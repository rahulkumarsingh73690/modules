<template>
  <div>
    <p>{{ projects.name }}</p>
    <p class="text-gray-500 group-hover:text-gray-800">
      {{ projects.description }}
    </p>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const projects = await $content(params.slug).fetch();

    return {
      projects,
    };
  },
};
</script>

<style>
.nuxt-content h1 {
  margin-bottom: 20px;
  margin-top: 20px;
}
.nuxt-content h2 {
  margin-bottom: 20px;
  margin-top: 20px;
}
.nuxt-content h3 {
  margin-bottom: 20px;
  margin-top: 20px;
}
.nuxt-content p {
  margin-bottom: 20px;
  margin-top: 20px;
}
.fixed {
  position: fixed;
}
</style>