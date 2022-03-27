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
      <h1>Login</h1>
    </div>

    <div>
      <v-layout column>
        <v-flex>
          <v-text-field
            v-model="email"
            name="email"
            label="Email"
            type="email"
            required
          ></v-text-field>
        </v-flex>
        <v-flex>
          <v-text-field
            v-model="password"
            name="password"
            label="Senha"
            type="password"
            required
          ></v-text-field>
        </v-flex>
        <v-flex class="text-xs-center" mt-5>
          <v-btn @click="login">Entrar</v-btn>
        </v-flex>
      </v-layout>
    </div>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    email: '',
    password: '',
    cpf: '',
  }),
  methods: {
    async login() {
      const data = {
        email: this.email,
        password: this.password,
        cpf: '',
        id: '',
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
            this.$router.push('/')
          }
        })
        .catch()
    },
  },
}
</script>
