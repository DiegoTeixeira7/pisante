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
  data: () => ({
    page: 1,
    items: [
      {
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
      {
        title: 'Produto 2',
        slug: '/produto-2',
        price: 162.33,
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
      {
        title: 'Produto 3',
        slug: '/produto-3',
        price: 112.13,
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
      {
        title: 'Produto 4',
        slug: '/produto-4',
        price: 195.98,
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
      {
        title: 'Produto 5',
        slug: '/produto-5',
        price: 195.98,
        availableQuantity: 10,
        page: 2,
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
    ],
  }),
  computed: {
    numberPages() {
      const number = Math.ceil(this.items.length / 4)
      return number
    },
  },
}
</script>
