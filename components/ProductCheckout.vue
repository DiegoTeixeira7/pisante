<template>
  <v-card class="mx-auto" max-width="400" outlined>
    <v-list-item>
      <v-list-item-content>
        <div class="text-overline mb-4">{{ item.title ? item.title : '' }}</div>
        <v-list-item-title class="text-h5 mb-1">
          R${{ item.price ? item.price : '0,00' }}
        </v-list-item-title>
        <v-list-item-subtitle>
          <span
            ><b>Tamanho:</b>
            {{
              item.model && item.model.inventory && item.model.inventory.size
                ? item.model.inventory.size
                : ''
            }}</span
          >
          <br />
          <span
            ><b>Cor:</b>
            {{
              item.model && item.model.inventory && item.model.inventory.color
                ? item.model.inventory.color
                : ''
            }}</span
          >
          <br />
          <span
            ><b>Quantidade:</b> {{ item.quantity ? item.quantity : 1 }}</span
          >
          <br />
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar tile size="80" color="grey"></v-list-item-avatar>
    </v-list-item>

    <v-switch
      v-model="packaging"
      :label="!packaging ? 'Convencional' : 'Presente'"
    ></v-switch>

    <v-card-actions>
      <v-btn outlined rounded text> Excluir </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data: () => ({
    packaging: false,
  }),
}
</script>

<style>
</style>
