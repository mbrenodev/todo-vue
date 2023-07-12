<template>
  <v-app id="inspire">
    <v-navigation-drawer 
      v-model="drawer" 
      app
    >
      <v-img
        src="https://picsum.photos/820/350"
        gradiente="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        dark
        class="pt-5 text-center"
      >
        <v-avatar size="100">
          <img
            
            src="https://github.com/mbrenodev.png"
            alt="avatar"
          >
        </v-avatar>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6"> Vue JS </v-list-item-title>
            <v-list-item-subtitle> Lista de tarefas </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-img>
      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      app
      prominent
      height="187"
      color="#fcb69f"
      dark
      src="https://picsum.photos/1800/720"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>
        <InputTarefa />
      </v-app-bar-title>

    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import InputTarefa from './components/InputTarefa';
export default {
  components: { InputTarefa },
  data: () => ({
    drawer: null,
    items: [
      { title: "Tarefas", icon: "mdi-view-dashboard", to: "/" },
      { title: "Sobre", icon: "mdi-help-box", to: "/sobre" },
    ],
    right: null,
  }),
};
</script>
