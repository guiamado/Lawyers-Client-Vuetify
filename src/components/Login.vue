<template>
  <v-container>
    <v-layout
      text-xs-center
      wrap
    >
      <v-flex mb-4>
        <h1 class="display-2 font-weight-bold mb-3">
          Welcome Lawyer!
        </h1>
        <p class="subheading font-weight-regular">
          To use the system, please login!
        </p>
      </v-flex>
      <v-flex mb-5
        xs12>
        <v-form v-model="valid">
          <v-text-field
            v-model="name"
            :rules="nameRules"
            :counter="10"
            label="Name"
            required
          ></v-text-field>
          <v-text-field
            v-model="password"
            :rules="passwordRules"
            label="Password"
            type="password"
            required
          ></v-text-field>
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-form>
        <v-btn 
          :disabled="!valid"
          @click="submit">Login</v-btn>
        <v-btn @click="clear">Clear</v-btn>
      </v-flex>
      <v-flex
        mb-5
        xs12
      >
        <h2 class="headline font-weight-bold mb-3">Where is the source code?</h2>

        <v-layout justify-center>
          <a
            v-for="(next, i) in whatsNext"
            :key="i"
            :href="next.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ next.text }}
          </a>
        </v-layout>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
  export default {
    name: ['Login'],
    data: () => ({
      whatsNext: [
        {
          text: 'Source Code',
          href: 'https://github.com/guiamado/Lawyers-Client-Vuetify'
        },
      ],
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => v.length <= 10 || 'Name must be less than 10 characters'
      ],
      password: '',
      passwordRules: [
        v => !!v || 'Password is required',
        v => v.length > 6 || 'Password must be more than 6 characters'
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid'
      ],
    }),
    methods: {
      submit () {
        console.log('enviado');
      },
      clear () {
        this.name = '';
        this.password = '';
        this.email = '';
      },
    },
  };
</script>

<style>

</style>
