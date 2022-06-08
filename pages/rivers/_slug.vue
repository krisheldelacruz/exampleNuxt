<template>
  <article>
    <h1>{{ river.title }}</h1>
    <p v-if="$fetchState.pending">
      <span class="loading"></span>
    </p>
    <p v-else-if="$fetchState.error">Error while fetching rivers 🤬</p>
    <section>
      <img :src="river.image" :alt="river.title" />
      <p>{{ river.description }}</p>
    </section>
    <button @click="goBack">Back</button>
  </article>
</template>
<script>
export default {
  data() {
    return {
      river: {}
    }
  },
  async fetch() {
    this.river = await fetch(
      `https://api.nuxtjs.dev/rivers/${this.$route.params.slug}`
    ).then(res => 
    res.json())
  },
  methods: {
    goBack() {
      return this.$router.go(-1)
    }
  }
}
</script>
<style scoped>

</style>
