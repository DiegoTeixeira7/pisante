<template>
  <div class="tw-m-8">
    <div
      v-if="user && user.role === 'admin' && !isAddProduct"
      class="tw-mt-2 tw-mb-2"
    >
      <v-btn outlined rounded text @click="isAddProduct = true">
        Adicionar produto
      </v-btn>
    </div>
    <div v-if="user && user.role === 'admin' && isAddProduct">
      <div class="tw-container tw-flex tw-flex-col">
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="product.brand"
            name="brand"
            label="Marca"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="product.material"
            name="material"
            label="Material"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col">
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              v-model="product.intended_audience"
              name="intended_audience"
              label="Público alvo"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              v-model="product.closure"
              name="closure"
              label="Fechamento"
              type="text"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-checkbox
              v-model="product.is_shock_absorbers"
              label="Possui amortecedores"
            ></v-checkbox>
            <v-checkbox
              v-model="product.is_anti_odour_insole"
              label="Possui palmilhas anti odor"
            ></v-checkbox>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              v-model="product.title"
              name="title"
              label="Título"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              v-model="product.price"
              name="price"
              label="Preço"
              type="number"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              v-model="product.slug"
              name="slug"
              label="slug"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              v-model="product.available_quantity"
              name="available_quantity"
              label="Quantidade em estoque"
              type="text"
              required
            ></v-text-field>
          </div>
        </div>
        <v-btn outlined rounded text @click="addProduct">
          Cadastrar produto
        </v-btn>
      </div>
    </div>
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
  data: () => ({
    user: {},
    isAddProduct: false,
    product: {
      brand: '',
      material: '',
      intended_audience: '',
      closure: '',
      is_shock_absorbers: null,
      is_anti_odour_insole: null,
      title: '',
      price: null,
      slug: '',
      available_quantity: null,
      id: '',
    },
  }),
  computed: {
    numberPages() {
      const number = Math.ceil(this.items.length / 4)
      return number
    },
  },
  mounted() {
    this.user = localStorage.getItem('user')
      ? JSON.parse(localStorage.getItem('user'))
      : {}
  },
  methods: {
    async addProduct() {
      this.product.price = parseInt(this.product.price)
      this.product.is_shock_absorbers = this.product.is_shock_absorbers ? 1 : 0
      this.product.is_anti_odour_insole = this.product.is_anti_odour_insole
        ? 1
        : 0

      const formData = new FormData()

      for (const key in this.product) {
        formData.append(key, this.product[key])
      }

      await this.$axios
        .post('/api/public_html/api/product/', formData)
        .then((res) => {
          const data =
            res.data && res.data.data && res.data.data.length > 0
              ? res.data.data[0]
              : null

          if (data && data.id) {
            this.isAddProduct = false
            window.location.reload(true)
          }
        })
        .catch()
    },
  },
}
</script>
