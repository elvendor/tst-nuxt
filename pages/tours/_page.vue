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
    <NuxtLink :to="`/tours/6`">6</NuxtLink>
    <NuxtLink :to="`/tours/7`">7</NuxtLink>
    <NuxtLink :to="`/tours/8`">8</NuxtLink>
    <NuxtLink :to="`/tours/9`">9</NuxtLink>
    <NuxtLink :to="`/tours/10`">10</NuxtLink>
    <NuxtLink :to="`/tours/11`">11</NuxtLink>
    <NuxtLink :to="`/tours/12`">12</NuxtLink>
    <NuxtLink :to="`/tours/13`">13</NuxtLink>
    <NuxtLink :to="`/tours/14`">14</NuxtLink>
    <NuxtLink :to="`/tours/15`">15</NuxtLink>
    <NuxtLink :to="`/tours/16`">16</NuxtLink>
    <NuxtLink :to="`/tours/17`">17</NuxtLink>
    <NuxtLink :to="`/tours/18`">18</NuxtLink>
    <NuxtLink :to="`/tours/19`">19</NuxtLink>
    <NuxtLink :to="`/tours/20`">20</NuxtLink>
  </div>
</template>
<script>
export default {
  name: 'IndexPage',
  async asyncData(context) {
    try {
      const { data } = await context.app.$axios.get(
        `http://api.test/b2c/tours/search?page=${context.params.page}`
      )
      console.log(data)
      return { tours: data.data }
    } catch (e) {
      context.error(e)
    }
  }
}
</script>
