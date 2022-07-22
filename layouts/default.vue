<template>
  <v-app>
    <v-app-bar app color="primary" dark>
     
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Demo</v-toolbar-title>
      
    </v-app-bar>

    <v-card>
      <v-navigation-drawer app v-model="drawer">
       
        <template v-slot:append v-if="guest">
          <div class="pa-2">
            <v-btn block color="red" dark>
              <v-icon left>mdi-lock</v-icon>
              Logout
            </v-btn>
          </div>
        </template>

        <v-list-item v-if="guest">
          <v-list-item-avatar>
            <v-img src="https://randomuser.me/api/portraits/men/78.jpg"></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>John Leider</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>





        <v-list>
          <v-list-item v-for="(item, index) in menus" :key="`menu-` + index" :to="item.route">
            <v-list-item-icon>
              <v-icon left>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>

      </v-navigation-drawer>
    </v-card>

    <v-content>
      <v-container fluid>
        <v-slide-y-transition>
          <Nuxt/>
        </v-slide-y-transition>

      </v-container>
    </v-content>

    <v-card>
      <v-footer absolute app>
        <v-card-text class="text-center">
          &copy; {{ new Date().getFullYear() }} — <strong>{{ appName }}</strong>
        </v-card-text>
      </v-footer>
    </v-card>


  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    drawer: true,
    menus: [
      { title: 'Home', icon: 'mdi-home', route: '/' },
      { title: 'Inspire', icon: 'mdi-home', route: '/inspire' },
      // { title: 'About', icon: 'mdi-account', route: '/about' },
    ],
    guest: true,
  }),
};
</script>
