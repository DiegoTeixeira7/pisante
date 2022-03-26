<template>
  <div
    class="
      tw-w-full
      lg:tw-ml-8
      tw-mt-4 tw-flex
      w-flex-row
      tw-justify-items-center
    "
  >
    <div>
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
                item && item.is_shock_absorbers ? 'Possui' : 'Não possui'
              }}</span
            >
            <br />
            <span
              ><b>Palmilha anti-odor:</b>
              {{
                item && item.is_anti_odour_insole ? 'Possui' : 'Não possui'
              }}</span
            >
          </div>
        </v-card-text>

        <v-divider class="mx-4"></v-divider>

        <v-card-actions>
          <v-btn color="deep-purple lighten-2" text>
            Adicionar no carrinho
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
    <div class="lg:tw-ml-4">
      <span><b>Escolha uma variação:</b></span>

      <div class="tw-mt-2">
        <p>{{ 'Tamanho' }}</p>
        <v-radio-group v="selectedSize" row>
          <v-radio
            v-for="(inventory, index) in item.inventory"
            :key="index"
            :label="inventory.size"
            :value="index"
          >
          </v-radio>
        </v-radio-group>
      </div>

      <div class="tw-mt-2">
        <p>{{ 'Cor' }}</p>
        <v-radio-group v="selectedColor" row>
          <v-radio
            v-for="(inventory, index) in item.inventory"
            :key="index"
            :label="inventory.color"
            :value="index"
          >
          </v-radio>
        </v-radio-group>
      </div>
      <div class="tw-mt-2">
        <p>{{ 'Quantidade' }}</p>
        <v-text-field
          v="selectedAmount"
          type="number"
          required
          min="0"
          max="10"
        ></v-text-field>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const productId = params.product
    let item = {}

    const inventory = [
      {
        quantity: 4,
        size: 38,
        color: 'Azul',
      },
      {
        quantity: 4,
        size: 39,
        color: 'Preto',
      },
      {
        quantity: 2,
        size: 40,
        color: 'Branco',
      },
    ]

    await $axios
      .get(`/api/public_html/api/product/${productId}`)
      .then((res) => {
        item = res?.data?.data[0]
        item.inventory = inventory
      })
      .catch()

    return { item }
  },
  data: () => ({
    selectedSize: null,
    selectedColor: null,
    selectedAmount: 1,
  }),
}
</script>

<style>
</style>
