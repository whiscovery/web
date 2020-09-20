<template>
    <v-toolbar-title>
       {{ title }}
       <v-btn icon @click="openDialog"><v-icon>mdi-grease-pencil</v-icon></v-btn>
       <v-dialog v-model="dialog" max-width="400">
         <v-card>
           <v-card-title>제목 수정</v-card-title>
           <v-card-text>
             <v-text-field v-model="text" />
           </v-card-text>
         </v-card>
       </v-dialog>

    </v-toolbar-title>
</template>

<script>
export default {
  props: ['title'],
  data () {
    return {
      dialog: false,
      text: this.title
    }
  },
  methods: {
    openDialog () {
      this.dialog = true
    }
  }
}
</script>
