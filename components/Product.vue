<template>
  <nuxt-link :to="item.slug">
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

      <!-- <v-card-actions>
        <v-btn color="deep-purple lighten-2" text>
          Adicionar no carrinho
        </v-btn>
      </v-card-actions> -->
    </v-card>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data: () => ({}),
  methods: {},
}
</script>
