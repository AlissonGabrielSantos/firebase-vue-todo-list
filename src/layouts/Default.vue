<template>
  <v-app>
    <v-app-bar app color="grey darken-4" dark elevation="1">
      <v-app-bar-nav-icon @click.stop="sidebar = !sidebar"></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-icon>mdi-account</v-icon>
    </v-app-bar>
  
    <v-navigation-drawer app color="grey darken-4" v-model="sidebar" :mini-variant.sync="mini">
      <v-list dense color="grey darken-4" dark>
        <v-list-item>
          <v-list-item-action>
            <v-icon @click.stop="sidebar = !sidebar">mdi-chevron-left</v-icon>
          </v-list-item-action>
          <v-list-item-title><h3>My ToDo List</h3></v-list-item-title>
        </v-list-item>
      </v-list>

      <v-divider color="grey"></v-divider>
        
        <v-list-item dark class="px-2" @click="mini = !mini">
          <v-list-item-avatar><v-icon>mdi-account</v-icon></v-list-item-avatar>
          <v-list-item-content>User</v-list-item-content>
          <v-btn icon small><v-icon>mdi-chevron-left</v-icon></v-btn>
        </v-list-item>
      
      <v-divider color="grey"></v-divider>
      
      <v-list dark>
        <v-list-item v-for="item of items" :key="item.title" link :to="item.to">
          <v-list-item-icon><v-icon>{{item.icon}}</v-icon></v-list-item-icon>
          <v-list-item-content>{{item.title}}</v-list-item-content>
        </v-list-item>
      </v-list>
    
    </v-navigation-drawer>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer app dark class="py-2"><span class="caption">MyToDoList &copy;2021</span></v-footer>
  </v-app>
</template>

<script>
export default {
  data(){
    return{
      sidebar: true,
      mini: false,
      items: [
        { title: "Home", icon:"mdi-home", to:"/"},
        { title: "Perfil", icon:"mdi-account-cog", to:"/perfil"},
        { title: "Sair", icon:"mdi-exit-to-app", to:"/login"},
      ]
    };
  },
};
</script>

<style> 
</style>