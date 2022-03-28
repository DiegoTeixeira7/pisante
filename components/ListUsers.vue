<template>
  <v-card class="mx-auto" max-width="600" outlined>
    <div v-if="!isEditUser">
      <v-list-item>
        <v-list-item-content>
          <v-list-item-subtitle>
            <span
              ><b>Nome:</b> {{ user.first_name ? user.first_name : '' }}</span
            >
            <br />
            <span
              ><b>Sobrenome:</b>
              {{ user.last_name ? user.last_name : '' }}</span
            >
            <br />
            <span><b>Telefone:</b> {{ user.phone ? user.phone : '' }}</span>
            <br />
            <span><b>Celular:</b> {{ user.cel ? user.cel : '' }}</span>
            <br />
            <span><b>Email:</b> {{ user.email ? user.email : '' }}</span>
            <br />
            <span><b>Gênero:</b> {{ user.gender ? user.gender : '' }}</span>
            <br />
            <span><b>CPF:</b> {{ user.cpf ? user.cpf : '' }}</span>
            <br />
            <span
              ><b>Tipo de usuário:</b> {{ user.role ? user.role : '' }}</span
            >
            <br />
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
        <v-btn outlined rounded text @click="isEditUser = true"> Editar </v-btn>
      </v-card-actions>
    </div>
    <div v-else>
      <div class="tw-flex tw-flex-col">
        <div class="tw-flex tw-flex-col">
          <v-text-field
            v-model="user_curr.first_name"
            name="name"
            label="Nome"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="user_curr.last_name"
            name="lastName"
            label="Sobrenome"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col tw-gap-x-4">
          <v-text-field
            v-model="user_curr.phone"
            name="phone"
            label="Telefone"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="user_curr.cel"
            name="cel"
            label="Celular"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col tw-gap-x-4">
          <div>
            <span>Gênero</span>
            <v-radio-group v-model="user_curr.gender" row>
              <v-radio label="Masculino" value="M"></v-radio>
              <v-radio label="Feminino" value="F"></v-radio>
            </v-radio-group>
          </div>
          <div class="lg:tw-mt-4 lg:tw-ml-auto">
            <v-text-field
              v-model="user_curr.cpf"
              name="cpf"
              label="CPF"
              type="text"
              required
            ></v-text-field>
          </div>
        </div>
        <div class="lg:tw-w-1/2">
          <v-text-field
            v-model="user_curr.cep"
            name="cep"
            label="Cep"
            type="text"
            required
          ></v-text-field>
        </div>

        <div class="tw-flex tw-flex-col tw-gap-x-4">
          <v-text-field
            v-model="user_curr.street"
            name="street"
            label="Rua"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="user_curr.city"
            name="city"
            label="Cidade"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col tw-gap-x-4">
          <v-text-field
            v-model="user_curr.number"
            name="number"
            label="Número"
            type="number"
            required
          ></v-text-field>
          <v-text-field
            v-model="user_curr.neighborhood"
            name="neighborhood"
            label="Bairro"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col tw-gap-x-4">
          <v-text-field
            v-model="user_curr.state"
            name="state"
            label="Estado"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="user_curr.country"
            name="country"
            label="País"
            type="text"
            required
          ></v-text-field>
        </div>
        <div>
          <v-text-field
            v-model="user_curr.email"
            name="email"
            label="Email"
            type="email"
            required
          ></v-text-field>
        </div>
        <v-btn outlined rounded text @click="editUser">
          Atualizar usuário
        </v-btn>
      </div>
    </div>
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
  data: (instance) => ({
    isEditUser: false,
    user_curr: instance.user,
  }),
  watch: {
    user(v) {
      this.user_curr = v
    },
  },
  methods: {
    async editUser() {
      this.user_curr.id = parseInt(this.user_curr.id)
      this.user_curr.id_address = parseInt(this.user_curr.id_address)
      this.user_curr.number = parseInt(this.user_curr.number)

      const formData = new FormData()

      for (const key in this.user_curr) {
        formData.append(key, this.user_curr[key])
      }

      await this.$axios
        .post('/api/public_html/api/user/', formData)
        .then((res) => {
          const data =
            res.data && res.data.data && res.data.data.length > 0
              ? res.data.data[0]
              : null

          if (data && data.id) {
            this.isEditUser = false
            window.location.reload(true)
          }
        })
        .catch()
    },
  },
}
</script>

<style>
</style>
