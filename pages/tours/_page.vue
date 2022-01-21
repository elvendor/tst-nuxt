<template>
  <div>
    <div class="container flex flex-col mx-auto w-full items-center justify-center bg-white dark:bg-gray-800 rounded-lg shadow">
      <ul class="flex flex-col divide divide-y">
        <li v-for="(t, i) in tours" :key="i" class="flex flex-row mb-2 border-gray-100">
          <div class="shadow border select-none cursor-pointer flex flex-1 items-center p-4">
            <div class="flex flex-col w-10 h-10 justify-center items-center mr-4">
              <a href="#" class="block relative">
                <nuxt-picture
                :src="t.image"
                sizes="sm:15vw md:7vw lg:50px"
                format="webp"
                quality="60"
                :modifiers="{ roundCorner: '0:30' }"
                class="mx-auto object-cover rounded-full h-12 w-12"
                />
              </a>
            </div>
            <div class="flex-1 pl-1 mr-16">
              <div class="font-medium dark:text-white">
                <NuxtLink :to="`/tour/${t.slug}`">{{ t.name }}</NuxtLink>
              </div>
              <div class="text-gray-600 dark:text-gray-200 text-sm">
                {{ t.startLocation }}
              </div>
            </div>
            <div class="text-gray-600 dark:text-gray-200 text-xs">
              {{ t.price }} <small>{{ t.currency }}</small>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <a-pagination :default-current="currentPage" :total="total" @change="paginate" />
  </div>
</template>
<script>
export default {
  async asyncData(context) {
    try {
      const { data } = await context.app.$axios.get(
      `https://api.travelshopbooking.com/b2c/tours/search?page=${context.params.page}`
      )
      return {
      tours: data.data,
      total: data.meta.total,
      currentPage: Number(context.params.page)
      }
    } catch (e) {
      context.error(e)
    }
  },
  methods: {
    paginate(page) {
      this.$router.push({ path: `/tours/${page}` })
    }
  }
}
</script>
