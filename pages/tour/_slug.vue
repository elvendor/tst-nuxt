<template>
  <div class="flex h-screen">
    <div class="overflow-hidden shadow-lg rounded-lg h-90 w-60 md:w-80 cursor-pointer m-auto hover:shadow">
        <a href="#" class="w-full block h-full">
            <nuxt-picture
              :src="tour.images[0].high"
              sizes="sm:100vw md:50vw lg:400px"
              format="webp"
              quality="60"
              :modifiers="{ roundCorner: '0:30' }"
              class="max-h-40 w-full object-cover"
            />
            <div class="bg-white dark:bg-gray-800 w-full p-4">
                <p class="text-indigo-500 text-md font-medium">
                    {{ tour.category.name }}
                </p>
                <p class="text-gray-800 dark:text-white text-xl font-medium mb-2">
                    {{ tour.name }}
                </p>
                <p class="text-gray-400 dark:text-gray-300 font-light text-md" v-html="tour.description"></p>
            </div>
        </a>
    </div>
  </div>
</template>

<script>
  export default {
    async asyncData(context) {
      const { data } = await context.app.$axios.get(
        `https://api.travelshopbooking.com/b2c/tours/${context.params.slug}`
      )
      return { tour: data }
    },
    head() {
      return {
        title: this.tour.name,
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: this.tour.meta_description
          }
        ]
      }
    }
  }
</script>