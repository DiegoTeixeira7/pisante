<template>
  <div class="tw-m-8 tw-flex tw-flex-col">
    <div
      class="
        tw-mt-4 tw-w-full tw-grid tw-gris-cols-1
        lg:tw-grid-cols-3
        tw-justify-items-center tw-gap-2
      "
    >
      <div v-for="(item, index) in items" :key="index">
        <product-checkout :item="item" />
      </div>
    </div>

    <div class="lg:tw-ml-10 tw-mt-4">
      <list-address :address="address" />
    </div>

    <div class="tw-mt-4 lg:tw-ml-10 tw-flex tw-flex-justify-items-center">
      <v-btn color="deep-purple lighten-2" text> Finalizar pedido </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    page: 1,
    items: [],
    address: {},
  }),
  mounted() {
    this.items = localStorage.getItem('cart')
      ? JSON.parse(localStorage.getItem('cart'))
      : []

    this.address = localStorage.getItem('user')
      ? JSON.parse(localStorage.getItem('user'))
      : {}
  },
}
</script>
<style>
</style>
