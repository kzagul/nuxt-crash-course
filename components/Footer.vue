<template>
    <v-footer
      :absolute="!fixed"
      app
      class="d-flex justify-center"
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      fixed: false,
    }
  }
}
</script>