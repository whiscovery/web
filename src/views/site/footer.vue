<template>
     <v-footer
      app
      color="primary"
      absolute
    >
      <v-spacer></v-spacer>
      <div>{{footer}} &copy; {{ new Date().getFullYear() }}</div>
      <v-btn fab dark color="cyan" @click="openDialog"><v-icon dark>mdi-pencil</v-icon></v-btn>

      <v-dialog v-model="dialog" persistent max-width="400px">
        <v-card>
          <v-card-title>
            Footer 수정
            <v-btn icon @click="save"><v-icon>mdi-content-save</v-icon></v-btn>
            <v-btn icon @click="dialog=false"><v-icon>mdi-close</v-icon></v-btn>
          </v-card-title>
          <v-card-text>
            <v-text-field v-model="text" hide-details @keypress.enter="save"></v-text-field>
          </v-card-text>
        </v-card>
      </v-dialog>
  </v-footer>
</template>

<script>
export default {
  props: ['footer'],
  data () {
    return {
      dialog: false,
      text: this.footer
    }
  },
  methods: {
    openDialog () {
      this.dialog = true
    },
    async save () {
      try {
        await this.$firebase.database().ref().child('site').update({ footer: this.text })
      } catch (e) {
        console.log(e.message)
      } finally {
        this.dialog = false
      }
    }
  }
}
</script>
