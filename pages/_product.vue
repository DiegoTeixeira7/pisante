<template>
  <div
    class="
      tw-w-full tw-m-4 tw-flex tw-flex-col
      lg:tw-flex-row
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
              ><b>Marca:</b>
              {{ item.model && item.model.brand ? item.model.brand : '' }}</span
            >
            <br />
            <span
              ><b>Material:</b>
              {{
                item.model && item.model.material ? item.model.material : ''
              }}</span
            >
            <br />
            <span
              ><b>Público:</b>
              {{
                item.model && item.model.intendedAudience
                  ? item.model.intendedAudience
                  : ''
              }}</span
            >
            <br />
            <span
              ><b>Fechamento:</b>
              {{
                item.model && item.model.closure ? item.model.closure : ''
              }}</span
            >
            <br />
            <span
              ><b>Amortecedores:</b>
              {{
                item.model && item.model.isShockAbsorbers
                  ? 'Possui'
                  : 'Não possui'
              }}</span
            >
            <br />
            <span
              ><b>Palmilha anti-odor:</b>
              {{
                item.model && item.model.isAntiOdourInsole
                  ? 'Possui'
                  : 'Não possui'
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
        <v-radio-group v-model="selectedSize" row>
          <v-radio
            v-for="(inventory, index) in item.model.inventory"
            :key="index"
            :label="inventory.size"
            :value="index"
          >
          </v-radio>
        </v-radio-group>
      </div>

      <div class="tw-mt-2">
        <p>{{ 'Cor' }}</p>
        <v-radio-group v-model="selectedColor" row>
          <v-radio
            v-for="(inventory, index) in item.model.inventory"
            :key="index"
            :label="inventory.color"
            :value="index"
          >
          </v-radio>
        </v-radio-group>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    item: {
      title: 'Produto 1',
      slug: '/produto-1',
      price: 122.33,
      availableQuantity: 10,
      page: 1,
      model: {
        brand: 'Nike',
        material: 'Couro',
        intendedAudience: 'Masculino',
        closure: 'Cadarço',
        isShockAbsorbers: true,
        isAntiOdourInsole: true,
        inventory: [
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
        ],
      },
    },
    selectedSize: null,
    selectedColor: null,
  }),
}
</script>

<style>
</style>
