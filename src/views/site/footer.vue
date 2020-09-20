<template>
     <v-footer
      app
      color="primary"
      absolute
    >
      <v-spacer></v-spacer>
      <div>{{footer}} &copy; {{ new Date().getFullYear() }}</div>
  </v-footer>
</template>

<script>
export default {
  props: ['footer']
}
</script>
