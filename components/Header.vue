<template>
    <div>
        <v-navigation-drawer
            v-model="drawer"
            :mini-variant="!miniVariant"
            :clipped="clipped"
            src="https://i.imgur.com/SRv4doc.gif"
            fixed
            app
            temporary
            expand-on-hover
        >
        <v-list>
            <v-list-item
                v-for="(item, i) in items"
                :key="i"
                :to="item.to"
                router
                exact
            >
            <v-list-item-action>
                <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
                <v-list-item-title v-text="item.title" />
            </v-list-item-content>
            </v-list-item>
        </v-list>
        </v-navigation-drawer>
        <v-app-bar
            :clipped-left="clipped"
            fixed
            app
        >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" />

        <v-btn to="/" nuxt depressed plain>
          <v-toolbar-title v-text="title"/>
        </v-btn>

        <nuxt-link to="/">
          home
        </nuxt-link>

        <v-spacer />

        <div v-if="!hasToken">
          <nuxt-link to="/login">
            Вход
          </nuxt-link>
        </div>
        <div v-if="hasToken">
          <a @click.prevent="logout" to="#">
            Выйти
          </a>
        </div>

        <v-btn icon>
            <v-icon>mdi-gmail</v-icon>
        </v-btn>

        <v-btn icon>
            <v-icon>mdi-github</v-icon>
        </v-btn>
        
        </v-app-bar>
    </div>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-code-braces',
          title: 'My projects',
          to: '/inspire'
        },
        {
          icon: 'mdi-layers-triple',
          title: 'My stack',
          to: '/stack'
        },
        {
          icon: 'mdi-account',
          title: 'users',
          to: '/users'
        },
        
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Kzagul personal website',
    }
  },
  computed: {
    hasToken(){
      return this.$store.getters.hasToken
    }
  },
  methods: {
    logout(){
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  }
}
</script>