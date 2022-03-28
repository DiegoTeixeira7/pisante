<template>
  <v-container
    class="
      tw-mt-8
      tw-w-full
      tw-h-full
      tw-flex
      tw-flex-col
      tw-items-center
      tw-justify-items-center
    "
  >
    <div>
      <h1>Registrar</h1>
    </div>

    <div>
      <div class="tw-flex tw-flex-col">
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="firstName"
            name="name"
            label="Nome"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="lastName"
            name="lastName"
            label="Sobrenome"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="phone"
            name="phone"
            label="Telefone"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="cel"
            name="cel"
            label="Celular"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <div>
            <span>Gênero</span>
            <v-radio-group v-model="gender" row>
              <v-radio label="Masculino" value="M"></v-radio>
              <v-radio label="Feminino" value="F"></v-radio>
            </v-radio-group>
          </div>
          <div class="lg:tw-mt-4 lg:tw-ml-auto">
            <v-text-field
              v-model="cpf"
              name="cpf"
              label="CPF"
              type="text"
              required
            ></v-text-field>
          </div>
        </div>
        <div class="lg:tw-w-1/2">
          <v-text-field
            v-model="cep"
            name="cep"
            label="Cep"
            type="text"
            required
          ></v-text-field>
        </div>

        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="street"
            name="street"
            label="Rua"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="city"
            name="city"
            label="Cidade"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="number"
            name="number"
            label="Número"
            type="number"
            required
          ></v-text-field>
          <v-text-field
            v-model="neighborhood"
            name="neighborhood"
            label="Bairro"
            type="text"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="state"
            name="state"
            label="Estado"
            type="text"
            required
          ></v-text-field>
          <v-text-field
            v-model="country"
            name="country"
            label="País"
            type="text"
            required
          ></v-text-field>
        </div>
        <div>
          <v-text-field
            v-model="email"
            name="email"
            label="Email"
            type="email"
            required
          ></v-text-field>
        </div>
        <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
          <v-text-field
            v-model="password"
            name="password"
            label="Senha"
            type="password"
            required
          ></v-text-field>
          <v-text-field
            v-model="passwordConfirmed"
            name="passwordConfirmed"
            label="Confirmar senha"
            type="password"
            required
          ></v-text-field>
        </div>
        <div>
          <v-checkbox
            v-model="acceptCookies"
            label="Aceito os cookies"
          ></v-checkbox>
        </div>
        <v-flex class="text-xs-center" mt-5>
          <v-btn @click="register">Cadastrar</v-btn>
        </v-flex>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    acceptCookies: false,
    firstName: '',
    lastName: '',
    phone: '',
    cel: '',
    gender: '',
    cpf: '',
    cep: '',
    street: '',
    city: '',
    number: null,
    neighborhood: '',
    state: '',
    country: '',
    email: '',
    password: '',
    passwordConfirmed: '',
  }),
  methods: {
    async register() {
      const data = {
        first_name: this.firstName,
        last_name: this.lastName,
        phone: this.phone,
        cel: this.cel,
        gender: this.gender,
        cpf: this.cpf,
        cep: this.cep,
        street: this.street,
        city: this.city,
        number: this.number,
        neighborhood: this.neighborhood,
        state: this.state,
        country: this.country,
        email: this.email,
        password: this.password,
        id: '',
      }

      if (this.acceptCookies) {
        localStorage.setItem(
          'acceptCookies',
          JSON.stringify(this.acceptCookies)
        )
      }

      const formData = new FormData()

      for (const key in data) {
        formData.append(key, data[key])
      }

      await this.$axios
        .post('/api/public_html/api/user/', formData)
        .then((res) => {
          const data =
            res.data && res.data.data && res.data.data.length > 0
              ? res.data.data[0]
              : null

          if (data && data.id) {
            localStorage.setItem('user', JSON.stringify(data))
            this.$router.push(
              {
                path: '/',
                force: true,
              },
              () => {
                window.location.reload(true)
              }
            )
          }
        })
        .catch()
    },
  },
}
</script>
