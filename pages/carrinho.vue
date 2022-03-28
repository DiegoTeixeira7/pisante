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
      <v-btn color="deep-purple lighten-2" text @click="finishOrder">
        Finalizar pedido
      </v-btn>
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
  methods: {
    async finishOrder() {
      let total = 0
      let products = ''
      let date = new Date()
      const hour = date.getHours()
      date = date.getFullYear() + '-' + date.getMonth() + '-' + date.getDay()

      for (const item of this.items) {
        total += item.price * item.amount
        products += item.id + ','
      }

      products = products.substring(0, products.length - 1)

      const order = {
        total,
        products,
        date,
        hour,
        id_user: parseInt(this.address.id),
        street: this.address.street,
        city: this.address.city,
        state: this.address.state,
        cep: this.address.cep,
        country: this.address.country,
        number: this.address.number,
        neighborhood: this.address.neighborhood,
      }

      const formData = new FormData()

      for (const key in order) {
        formData.append(key, order[key])
      }

      await this.$axios
        .post('/api/public_html/api/order/', formData)
        .then((res) => {
          const data =
            res.data && res.data.data && res.data.data.length > 0
              ? res.data.data[0]
              : null

          if (data && data.id) {
            localStorage.setItem('cart', JSON.stringify([]))
            this.$router.push(
              {
                path: '/',
                force: true,
              },
              () => {
                this.$router.app.refresh()
              }
            )
          }
        })
        .catch()
    },
  },
}
</script>
<style>
</style>
