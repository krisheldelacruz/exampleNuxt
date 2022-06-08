<template>
  <div>
    <h1>Data fetched using asyncData</h1>
    <ul>
      <li v-for="river in rivers" :key="river.title">
        <NuxtLink
          :to="{ name: 'rivers-slug', params: { slug: river.slug } }"
        >
          {{ river.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios }) {
    const rivers = await $axios.$get('https://api.nuxtjs.dev/rivers')
    return { rivers }
  }
}
</script>