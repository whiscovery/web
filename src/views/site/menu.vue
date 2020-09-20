<template>
  <div>
    <v-list>
      <v-list-group
        v-for="(item,i) in items"
        :key="i"
        v-model="item.active"
        :prepend-icon="item.icon"
        no-action
      >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item-content>
        </template>

        <v-list-item
          v-for="subItem in item.subitems"
          :key="subItem.title"
          :to="subItem.to"
        >
          <v-list-item-content>
            <v-list-item-title v-text="subItem.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-group>
    </v-list>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          title: 'home',
          to: '/',
          active: true,
          icon: 'mdi-home'
        },
        {
          title: 'about',
          to: '/about',
          subitems: [
            {
              title: 'Scotch whiskey',
              to: '/ScotchWhiskey'
            }

          ]
        },
        {
          title: 'category',
          to: '/category'
        }

      ]
    }
  }

}
</script>
