<template>
<div>
  <ul>
  <li><NuxtLink to="/about">About</NuxtLink></li>
  <li><NuxtLink to="/axiosExample">AsyncData Hook Example</NuxtLink></li>
  <li><NuxtLink to="/fetchExample">Fetch Hook Example</NuxtLink></li>
  </ul>
</div>
</template>


<script>
import Rivers from '../components/Rivers.vue'
export default {
  components: { Rivers },
  name: 'IndexPage',
  async asyncData() {
    const rivers = await fetch(
      'https://api.nuxtjs.dev/rivers'
    ).then((res) => res.json())

    return { rivers }
  
}
}
</script>
<style >
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
li {
    display: block;
    width: 200px;
    border: 10px solid white;
}
</style>