<script>
import { defineComponent, ref } from '@vue/composition-api'

export default defineComponent({
  setup() {
    const pageName = ref('用語集一覧')
    return {
      pageName,
    }
  },
})
</script>

<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center"> {{ pageName }} </v-card>
      <v-card> </v-card>
    </v-col>
  </v-row>
</template>
