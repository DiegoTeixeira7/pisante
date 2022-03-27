<template>
  <v-card class="mx-auto" max-width="400" outlined>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-subtitle>
          <span><b>Rua:</b> {{ user.street ? user.street : '' }}</span>
          <br />
          <span><b>Número:</b> {{ user.number ? user.number : '' }}</span>
          <br />
          <span><b>Cidade:</b> {{ user.city ? user.city : '' }}</span>
          <br />
          <span><b>Estado:</b> {{ user.state ? user.state : '' }}</span>
          <br />
          <span><b>País:</b> {{ user.country ? user.country : '' }}</span>
          <br />
          <span
            ><b>Bairro:</b>
            {{ user.neighborhood ? user.neighborhood : '' }}</span
          >
          <br />
          <span><b>Cep:</b> {{ user.cep ? user.cep : '' }}</span>
          <br />
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar tile size="80" color="grey"></v-list-item-avatar>
    </v-list-item>

    <v-card-actions>
      <v-btn outlined rounded text @click="editUser"> Editar </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  data: () => ({}),
  methods: {
    editUser() {},
  },
}
</script>

<style>
</style>
