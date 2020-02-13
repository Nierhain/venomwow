<template>
    <v-toolbar app>
      <v-toolbar-side-icon class="hidden-md-and-up"></v-toolbar-side-icon>
      <v-toolbar-items class="links hidden-sm-and-down">
        <v-btn flat><router-link to="/">Home</router-link></v-btn>
        <!-- <v-btn flat><router-link to="/about">About</router-link></v-btn> -->
        <v-btn flat><router-link to="/guides">Guides</router-link></v-btn>
        <v-btn flat><router-link to="/roster">Roster</router-link></v-btn>
      </v-toolbar-items>
      <v-spacer></v-spacer>
      <v-toolbar-title class="headline text-uppercase">
        <span>Venom</span>
      </v-toolbar-title>
    </v-toolbar>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
          publicPath: process.env.BASE_URL
        }
    }
}
</script>

<style scoped>
.links a{
  text-decoration: none;
}
</style>
