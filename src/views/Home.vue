<template>
  <v-content>
    <Leaders />
    <v-container>
    <v-layout align-center justify-center row fill-height>
      <v-flex xs12 md3>
        <Quotes />
      </v-flex>
      <v-flex xs12 md4>
        <WarcraftLogs />
      </v-flex>
    </v-layout>
    </v-container>
  </v-content>
</template>

<script>

  export default {
    components: {
      WarcraftLogs: () => import('@/components/WarcraftLogs'),
      Leaders: () => import('@/components/Leaders'),
      Quotes: () => import('@/components/Quotes')
    }
  }
</script>
