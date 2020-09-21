<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
     <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
     <site-title :title="site.title"></site-title>

     <v-spacer></v-spacer>
     <v-btn icon @click="save"><v-icon>mdi-check</v-icon></v-btn>
     <v-btn icon @click="read"><v-icon>mdi-book</v-icon></v-btn>
     <v-btn icon @click="readOne"><v-icon>mdi-note</v-icon></v-btn>

    </v-app-bar>
     <v-navigation-drawer app v-model="drawer">
      <site-menu :items="site.menu"></site-menu>
     </v-navigation-drawer>

    <v-main>
      <router-view></router-view>
    </v-main>

   <site-footer :footer="site.footer"></site-footer>
  </v-app>
</template>

<script>
import SiteTitle from '@/components/title'
import SiteFooter from '@/components/footer'
import SiteMenu from '@/components/menu'

export default {
  components: { SiteTitle, SiteFooter, SiteMenu },
  name: 'App',
  data () {
    return {
      drawer: false,
      site: {
        title: 'Whiscovery',
        menu: [],
        footer: 'made by Whiscovery'
      }
    }
  },
  created () {
    this.subscribe()
  },
  methods: {
    subscribe () {
      this.$firebase.database().ref().child('site').on('value', sn => {
        const v = sn.val()
        if (!v) {
          this.$firebase.database().ref().child('site').set(this.site)
        }
        this.site = v
      }, (e) => {
        console.log(e.message)
      })
    },
    save () {
      this.$firebase.database().ref().child('abcd').set({
        title: 'abcd',
        text: 'tttt'
      })
    },
    read () {
      this.$firebase.database().ref().child('abcd').on('value', sn => {
        console.log(sn)
        console.log(sn.val())
      })
    },
    async readOne () {
      const sn = await this.$firebase.database().ref().child('abcd').once('value')
      console.log(sn.val())
    }
  }
}
</script>
