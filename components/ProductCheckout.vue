<template>
  <v-card class="mx-auto" max-width="400" outlined>
    <v-list-item>
      <v-list-item-content>
        <div class="text-overline mb-4">{{ item.title ? item.title : '' }}</div>
        <v-list-item-title class="text-h5 mb-1">
          R${{ item.price ? item.price : '0,00' }}
        </v-list-item-title>
        <v-list-item-subtitle>
          <span><b>Tamanho:</b> {{ item.size ? item.size : '' }}</span>
          <br />
          <span><b>Cor:</b> {{ item.color ? item.color : '' }}</span>
          <br />
          <span><b>Quantidade:</b> {{ item.amount ? item.amount : 1 }}</span>
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
      <v-btn outlined rounded text @click="excludeItem"> Excluir </v-btn>
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
  methods: {
    excludeItem() {
      const items = localStorage.getItem('cart')
        ? JSON.parse(localStorage.getItem('cart'))
        : []

      const data = []
      let exclude = false

      for (const i of items) {
        if (
          !exclude &&
          i.id === this.item.id &&
          i.color === this.item.color &&
          i.size === this.item.size &&
          i.amount === this.item.amount
        ) {
          exclude = true
        } else {
          data.push(i)
        }
      }

      localStorage.setItem('cart', JSON.stringify(data))
      window.location.reload(true)
    },
  },
}
</script>

<style>
</style>
