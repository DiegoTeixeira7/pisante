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
      <form>
        <v-layout column>
          <v-flex>
            <v-text-field
              id="email"
              name="email"
              label="Email"
              type="email"
              required
            ></v-text-field>
          </v-flex>
          <v-flex>
            <v-text-field
              id="password"
              name="password"
              label="Senha"
              type="password"
              required
            ></v-text-field>
          </v-flex>
          <v-flex class="text-xs-center" mt-5>
            <v-btn type="submit">Entrar</v-btn>
          </v-flex>
        </v-layout>
      </form>
    </div>
  </v-container>
</template>

<script>
export default {}
</script>
