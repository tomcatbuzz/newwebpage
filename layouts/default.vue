<template>
  <v-app light>
    <v-navigation-drawer
      v-model="drawer"
      app
      absolute
      temporary
      >
      <v-list>
        <v-list-tile
          router
          :to="item.to"
          :key="i"
          v-for="(item, i) in items"
          exact
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar fixed app color="primary" scroll-toolbar-off-screen scroll-threshold="200">
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn 
        flat
        to="/">
          <v-icon left>apps</v-icon>
          Home
        </v-btn>
        <v-btn 
        flat
        to="/about">
          <v-icon left>bubble_chart</v-icon>
          About
        </v-btn>
        <v-btn 
        flat
        to="/projects">
          <v-icon left>explore</v-icon>
          Projects
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
      <v-fab-transition>
              <v-btn
                v-show="!hidden"
                color="secondary"
                fab
                dark
                small
                fixed
                bottom
                right
              >
                <v-icon>add</v-icon>
              </v-btn>
            </v-fab-transition>
    </v-content>
    <v-footer app>
      <span>&copy; 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        hidden: false,
        drawer: null,
        items: [
          { icon: 'apps', title: 'Home', to: '/' },
          { icon: 'bubble_chart', title: 'About', to: '/about' },
          { icon: 'explore', title: 'Projects', to: '/projects' }
        ],
        title: 'Tomcatbuzz'
      }
    }
  }
</script>
