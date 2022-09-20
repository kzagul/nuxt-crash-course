<template>
  <v-form @submit.prevent="onSubmit" ref="form" v-model="valid" lazy-validation>
    <v-text-field
      v-model="name"
      filled
      :counter="10"
      :rules="nameRules"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="email"
      filled
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-text-field
      v-model="password"
      filled
      color="deep-purple"
      counter="6"
      label="Password"
      style="min-height: 96px"
      type="password"
    ></v-text-field>

    <div class="buttons d-flex flex-column">
      <v-btn large to="/" class="mb-6" nuxt depressed plain>
        На главную страницу
      </v-btn>

      <v-btn
        large
        :disabled="!valid"
        color="success"
        class="mr-4"
        
        type="submit"
      >
        Войти
      </v-btn>
    </div>
  </v-form>
</template>

<script>
export default {
  layout: "empty",
  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
    ],
    email: "",
    password: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    select: null,
    items: ["Item 1", "Item 2", "Item 3", "Item 4"],
  }),

  methods: {
    validate() {
      this.$refs.form.validate();
    },
    onSubmit() {
      this.$store.dispatch('login')
      this.$router.push('/')
      
    }
  },
};
</script>

