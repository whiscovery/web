<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
     <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
     <site-title :title="title"></site-title>

     <v-spacer></v-spacer>
     <v-btn icon to="/about">
       <v-icon>mdi-magnify</v-icon>
     </v-btn>

    </v-app-bar>
     <v-navigation-drawer app v-model="drawer">
       <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Application
          </v-list-item-title>
          <v-list-item-subtitle>
            subtitle
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>
      <site-menu></site-menu>
     </v-navigation-drawer>
    <!-- contents 영역 -->
    <v-content>
      <router-view></router-view>
    </v-content>

   <site-footer :footer="footer"></site-footer>
  </v-app>
</template>

<script>
import SiteTitle from '@/views/site/title'
import SiteFooter from '@/views/site/footer'
import SiteMenu from '@/views/site/menu'

export default {
  components: { SiteTitle, SiteFooter, SiteMenu },
  name: 'App',
  data () {
    return {
      drawer: false,
      title: 'Whiscovery',
      item: [],
      footer: 'made by Whiscovery'
    }
  }
}
</script>
