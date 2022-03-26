<template>
  <div class="tw-m-8">
    <div
      class="
        tw-mt-4 tw-w-full tw-grid tw-grid-cols-1
        lg:tw-grid-cols-2
        tw-justify-items-center tw-gap-2
      "
    >
      <div v-for="(item, index) in items" :key="index">
        <product v-if="item.page === page" :item="item" />
      </div>
    </div>
    <div class="text-center tw-mt-8">
      <v-pagination v-model="page" :length="numberPages" circle></v-pagination>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, error }) {
    const page = 1

    let data = []
    await $axios
      .get('/api/public_html/api/product/')
      .then((res) => {
        data = res?.data?.data
        let j = 1

        for (let i = 0; i < data.length; i++) {
          if (i !== 0 && i % 4 === 0) {
            j++
          }
          data[i].page = j
        }
      })
      .catch()
    return { page, items: data }
  },
  computed: {
    numberPages() {
      const number = Math.ceil(this.items.length / 4)
      return number
    },
  },
}
</script>
