<template>
  <div>
    <h1>{{ data.name }}</h1>
    <img :src="data.images[0].high" />
  </div>
</template>

<script>
  export default {
    async asyncData(context) {
      const { data } = await context.app.$axios.get(
        `https://api.travelshopbooking.com/b2c/tours/${context.params.slug}`
      )
      return { data }
    }
  }
</script>