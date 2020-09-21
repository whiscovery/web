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
          v-for="(subItem, j) in item.subitems"
          :key="j"
          :to="subItem.to"
        >
          <v-list-item-content>
            <v-list-item-title v-text="subItem.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-group>
      <v-list-item>
        <v-list-icon>
          <v-icon>mdi-plus</v-icon>
        </v-list-icon>
        <v-list-item-content>
          <v-list-item-title>추가하기</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

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
          title: '분류',
          to: '/category',
          subitems: [
            {
              title: '스카치 위스키',
              to: '/ScotchWhiskey'
            },
            {
              title: '블렌디드 위스키',
              to: '/BlendedWhiskey'
            }

          ]
        },
        {
          title: '스터디 입력',
          to: '/write'
        }

      ]
    }
  }

}
</script>
