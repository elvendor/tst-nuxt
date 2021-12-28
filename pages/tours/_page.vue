<template>
  <div>
    <ul>
      <li v-for="(t, i) in tours" :key="i">
        <NuxtLink :to="`/tour/${t.slug}`">{{ t.name }}</NuxtLink>
      </li>
    </ul>
    <NuxtLink :to="`/tours/1`">1</NuxtLink>
    <NuxtLink :to="`/tours/2`">2</NuxtLink>
    <NuxtLink :to="`/tours/3`">3</NuxtLink>
    <NuxtLink :to="`/tours/4`">4</NuxtLink>
    <NuxtLink :to="`/tours/5`">5</NuxtLink>
  </div>
</template>
<script>
export default {
  name: 'IndexPage',
  async asyncData(context) {
    try {
      const { data } = await context.app.$axios.get(
        `https://api.travelshopbooking.com/b2c/tours/search?page=${context.params.page}`
      )
      return { tours: data.data }
    } catch (e) {
      context.error(e)
    }
  }
}
</script>
