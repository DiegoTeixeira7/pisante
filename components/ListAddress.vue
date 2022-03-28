<template>
  <div>
    <div v-if="step === 1">
      <v-card class="mx-auto" max-width="400" outlined>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-subtitle>
              <span
                ><b>Rua:</b> {{ address.street ? address.street : '' }}</span
              >
              <br />
              <span
                ><b>Número:</b> {{ address.number ? address.number : '' }}</span
              >
              <br />
              <span><b>Cidade:</b> {{ address.city ? address.city : '' }}</span>
              <br />
              <span
                ><b>Estado:</b> {{ address.state ? address.state : '' }}</span
              >
              <br />
              <span
                ><b>País:</b> {{ address.country ? address.country : '' }}</span
              >
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
          <v-btn outlined rounded text @click="step = 2">
            Adicionar outro endereço
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
    <div v-else class="tw-container">
      <div class="tw-flex tw-flex-col">
        <div class="lg:tw-w-1/2">
          <v-text-field
            v-model="address_curr.cep"
            name="cep"
            label="Cep"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="address_curr.street"
            name="street"
            label="Rua"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="address_curr.city"
            name="city"
            label="Cidade"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="address_curr.number"
            name="number"
            label="Número"
            type="number"
            required
          ></v-text-field>
          <v-text-field
            v-model="address_curr.neighborhood"
            name="neighborhood"
            label="Bairro"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="address_curr.state"
            name="state"
            label="Estado"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="address_curr.country"
            name="country"
            label="País"
            type="text"
            required
          ></v-text-field>
        </div>
      </div>
      <v-btn outlined rounded text @click="editAddress">
        Salvar novo outro endereço de entrega
      </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    address: {
      type: Object,
      required: true,
    },
  },
  data: (instance) => ({
    step: 1,
    address_curr: instance.address,
  }),
  watch: {
    address(v) {
      this.address_curr = v
    },
  },
  methods: {
    editAddress() {
      localStorage.setItem('user', JSON.stringify(this.address_curr))
      this.step = 1
    },
  },
}
</script>

<style>
</style>
