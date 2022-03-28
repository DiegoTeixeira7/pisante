<template>
  <v-card class="mx-auto" max-width="400" outlined>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-subtitle>
          <span><b>Rua:</b> {{ address.street ? address.street : '' }}</span>
          <br />
          <span><b>Número:</b> {{ address.number ? address.number : '' }}</span>
          <br />
          <span><b>Cidade:</b> {{ address.city ? address.city : '' }}</span>
          <br />
          <span><b>Estado:</b> {{ address.state ? address.state : '' }}</span>
          <br />
          <span><b>País:</b> {{ address.country ? address.country : '' }}</span>
          <br />
          <span
            ><b>Bairro:</b>
            {{ address.neighborhood ? address.neighborhood : '' }}</span
          >
          <br />
          <span><b>Cep:</b> {{ address.cep ? address.cep : '' }}</span>
          <br />
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar tile size="80" color="grey"></v-list-item-avatar>
    </v-list-item>

    <v-card-actions>
      <v-btn outlined rounded text @click="addAddress">
        Adicionar outro endereço
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    address: {
      type: Object,
      required: true,
    },
  },
  data: () => ({}),
  methods: {
    addAddress() {
      console.log(this.address)
    },
  },
}
</script>

<style>
</style>
