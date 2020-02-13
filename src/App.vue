<template>
  <v-app>
    <Header />
    <v-container>
        <router-view />
    </v-container>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
    Header: () => import('@/components/core/Header')
  },
  data () {
    return {
      //
    }
  }
}
</script>
