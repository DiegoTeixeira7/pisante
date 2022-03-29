<template>
  <div>
    <div v-if="!isEditProduct">
      <nuxt-link :to="item.id">
        <v-card :loading="loading" class="mx-auto my-12" max-width="374">
          <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <img height="250" src="~/assets/images/tenis-nike.jpg" />

          <v-card-title>{{ item.title ? item.title : '' }}</v-card-title>

          <v-card-text>
            <div class="my-2 text-subtitle-1">
              R${{ item.price ? item.price : '0,00' }}
            </div>

            <div class="tw-mt-2">
              <span
                ><b>Marca:</b> {{ item && item.brand ? item.brand : '' }}</span
              >
              <br />
              <span
                ><b>Material:</b>
                {{ item && item.material ? item.material : '' }}</span
              >
              <br />
              <span
                ><b>Público:</b>
                {{
                  item && item.intended_audience ? item.intended_audience : ''
                }}</span
              >
              <br />
              <span
                ><b>Fechamento:</b>
                {{ item && item.closure ? item.closure : '' }}</span
              >
              <br />
              <span
                ><b>Amortecedores:</b>
                {{
                  item && item.is_shock_absorbers === 't'
                    ? 'Possui'
                    : 'Não possui'
                }}</span
              >
              <br />
              <span
                ><b>Palmilha anti-odor:</b>
                {{
                  item && item.is_anti_odour_insole === 't'
                    ? 'Possui'
                    : 'Não possui'
                }}</span
              >
            </div>
          </v-card-text>

          <v-divider class="mx-4"></v-divider>
        </v-card>
      </nuxt-link>

      <div v-if="user && user.role === 'admin'" class="tw-mt-2">
        <v-btn outlined rounded text @click="isEditProduct = true">
          Editar
        </v-btn>
      </div>
    </div>
    <div v-else>
      <div class="tw-flex tw-flex-col">
        <div class="tw-flex tw-flex-col">
          <v-text-field
            v-model="product_curr.brand"
            name="brand"
            label="Marca"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="product_curr.material"
            name="material"
            label="Material"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col">
          <v-text-field
            v-model="product_curr.intended_audience"
            name="intended_audience"
            label="Público alvo"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="product_curr.closure"
            name="closure"
            label="Fechamento"
            type="text"
            required
          ></v-text-field>
          <v-checkbox
            v-model="product_curr.is_shock_absorbers"
            label="Possui amortecedores"
          ></v-checkbox>
          <v-checkbox
            v-model="product_curr.is_anti_odour_insole"
            label="Possui palmilhas anti odor"
          ></v-checkbox>
          <v-text-field
            v-model="product_curr.title"
            name="title"
            label="Título"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="product_curr.price"
            name="price"
            label="Preço"
            type="number"
            required
          ></v-text-field>
          <v-text-field
            v-model="product_curr.slug"
            name="slug"
            label="slug"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="product_curr.available_quantity"
            name="available_quantity"
            label="Quantidade em estoque"
            type="text"
            required
          ></v-text-field>
        </div>
      </div>
      <v-btn outlined rounded text @click="editProduct">
        Atualizar produto
      </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data: (instance) => ({
    user: {},
    isEditProduct: false,
    product_curr: instance.item,
  }),
  watch: {
    item(v) {
      this.product_curr = v
    },
  },
  mounted() {
    this.user = localStorage.getItem('user')
      ? JSON.parse(localStorage.getItem('user'))
      : {}
  },
  methods: {
    async editProduct() {
      this.product_curr.id = parseInt(this.product_curr.id)
      this.product_curr.price = parseInt(this.product_curr.price)
      this.product_curr.is_shock_absorbers = this.product_curr
        .is_shock_absorbers
        ? 1
        : 0
      this.product_curr.is_anti_odour_insole = this.product_curr
        .is_anti_odour_insole
        ? 1
        : 0

      const formData = new FormData()

      for (const key in this.product_curr) {
        formData.append(key, this.product_curr[key])
      }

      await this.$axios
        .post('/api/public_html/api/product/', formData)
        .then((res) => {
          const data =
            res.data && res.data.data && res.data.data.length > 0
              ? res.data.data[0]
              : null

          if (data && data.id) {
            this.isEditProduct = false
            window.location.reload(true)
          }
        })
        .catch()
    },
  },
}
</script>
