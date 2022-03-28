<template>
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
          <span><b>Marca:</b> {{ item && item.brand ? item.brand : '' }}</span>
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
}
</script>
