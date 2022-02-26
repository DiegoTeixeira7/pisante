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
      <Address :address="address" />
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
    items: [
      {
        title: 'Produto 1',
        slug: '/produto-1',
        price: 122.33,
        quantity: 1,
        model: {
          brand: 'Nike',
          material: 'Couro',
          intendedAudience: 'Masculino',
          closure: 'Cadarço',
          isShockAbsorbers: true,
          isAntiOdourInsole: true,
          inventory: {
            size: 38,
            color: 'Azul',
          },
        },
      },
      {
        title: 'Produto 2',
        slug: '/produto-2',
        price: 162.33,
        quantity: 2,
        model: {
          brand: 'Nike',
          material: 'Couro',
          intendedAudience: 'Masculino',
          closure: 'Cadarço',
          isShockAbsorbers: true,
          isAntiOdourInsole: true,
          inventory: {
            size: 38,
            color: 'Azul',
          },
        },
      },
      {
        title: 'Produto 3',
        slug: '/produto-3',
        price: 112.13,
        quantity: 1,
        model: {
          brand: 'Nike',
          material: 'Couro',
          intendedAudience: 'Masculino',
          closure: 'Cadarço',
          isShockAbsorbers: true,
          isAntiOdourInsole: true,
          inventory: {
            size: 40,
            color: 'Branco',
          },
        },
      },
    ],
    address: {
      street: 'Rua 1',
      city: 'Viçosa',
      state: 'Minas Gerais',
      cep: '36570-000',
      country: 'Brasil',
      number: 12,
      neighborhood: 'Centro',
    },
  }),
}
</script>
<style>
</style>
