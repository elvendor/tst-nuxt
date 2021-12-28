<template>
  <div>
    <h1>{{ data.name }}</h1>
    <nuxt-picture
      :src="data.images[0].high"
      sizes="sm:100vw md:50vw lg:400px"
      format="webp"
      quality="60"
      :modifiers="{ roundCorner: '0:30' }"
    />
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