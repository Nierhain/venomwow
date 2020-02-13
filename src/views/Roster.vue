<template>
    <v-content>
        <Roster />
    </v-content>
</template>

<script>
export default {
  components: {
      Roster: () => import('@/components/Roster')
  }
}
</script>