<template>
  <v-card class="mx-auto" max-width="400" outlined>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-subtitle>
          <span
            ><b>Total: </b>R$ {{ order.total ? order.total : '' }} reais</span
          >
          <br />
          <span><b>Data:</b> {{ order.date ? order.date : '' }}</span>
          <br />
          <span><b>Hora:</b> {{ order.hour ? order.hour : '' }}</span>
          <br />
          <span
            ><b>Produtos:</b> {{ order.products ? order.products : '' }}</span
          >
          <br />
          <span
            ><b>Nome:</b> {{ order.first_name ? order.first_name : '' }}</span
          >
          <br />
          <span
            ><b>Sobrenome:</b>
            {{ order.last_name ? order.last_name : '' }}</span
          >
          <br />
          <span><b>Telefone:</b> {{ order.phone ? order.phone : '' }}</span>
          <br />
          <span><b>Celular:</b> {{ order.cel ? order.cel : '' }}</span>
          <br />
          <span><b>Email:</b> {{ order.email ? order.email : '' }}</span>
          <br />
          <span><b>CPF:</b> {{ order.cpf ? order.cpf : '' }}</span>
          <br />
          <span><b>Rua:</b> {{ order.street ? order.street : '' }}</span>
          <br />
          <span><b>Número:</b> {{ order.number ? order.number : '' }}</span>
          <br />
          <span><b>Cidade:</b> {{ order.city ? order.city : '' }}</span>
          <br />
          <span><b>Estado:</b> {{ order.state ? order.state : '' }}</span>
          <br />
          <span><b>País:</b> {{ order.country ? order.country : '' }}</span>
          <br />
          <span
            ><b>Bairro:</b>
            {{ order.neighborhood ? order.neighborhood : '' }}</span
          >
          <br />
          <span><b>Cep:</b> {{ order.cep ? order.cep : '' }}</span>
          <br />
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar tile size="80" color="grey"></v-list-item-avatar>
    </v-list-item>
  </v-card>
</template>

<script>
export default {
  props: {
    order: {
      type: Object,
      required: true,
    },
  },
  data: () => ({}),
}
</script>

<style>
</style>
