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
      <form>
        <div class="tw-flex tw-flex-col">
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              id="name"
              name="name"
              label="Nome"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              id="lastName"
              name="lastName"
              label="Sobrenome"
              type="text"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              id="telephone"
              name="telephone"
              label="Telefone"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              id="phone"
              name="phone"
              label="Celular"
              type="text"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <div>
              <span>Gênero</span>
              <v-radio-group row>
                <v-radio label="Masculino" value="m"></v-radio>
                <v-radio label="Feminino" value="f"></v-radio>
              </v-radio-group>
            </div>
            <div class="lg:tw-mt-4 lg:tw-ml-auto">
              <v-text-field
                id="cpf"
                name="cpf"
                label="CPF"
                type="text"
                required
              ></v-text-field>
            </div>
          </div>
          <div class="lg:tw-w-1/2">
            <v-text-field
              id="cep"
              name="cep"
              label="Cep"
              type="text"
              required
            ></v-text-field>
          </div>

          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              id="street"
              name="street"
              label="Rua"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              id="city"
              name="city"
              label="Cidade"
              type="text"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              id="number"
              name="number"
              label="Número"
              type="number"
              required
            ></v-text-field>
            <v-text-field
              id="neighborhood"
              name="neighborhood"
              label="Bairro"
              type="text"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              id="state"
              name="state"
              label="Estado"
              type="text"
              required
            ></v-text-field>
            <v-text-field
              id="country"
              name="country"
              label="País"
              type="text"
              required
            ></v-text-field>
          </div>
          <div>
            <v-text-field
              id="email"
              name="email"
              label="Email"
              type="email"
              required
            ></v-text-field>
          </div>
          <div class="tw-flex tw-flex-col lg:tw-flex-row tw-gap-x-4">
            <v-text-field
              id="password"
              name="password"
              label="Senha"
              type="password"
              required
            ></v-text-field>
            <v-text-field
              id="passwordConfirmed"
              name="passwordConfirmed"
              label="Confirmar senha"
              type="password"
              required
            ></v-text-field>
          </div>
          <v-flex class="text-xs-center" mt-5>
            <v-btn type="submit">Cadastrar</v-btn>
          </v-flex>
        </div>
      </form>
    </div>
  </v-container>
</template>

<script>
export default {}
</script>
