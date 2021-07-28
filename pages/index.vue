<script>
import {
  defineComponent,
  ref,
  computed,
  useContext,
} from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    // 用語集一覧データ
    const glossariesData = [
      { id: 1, name: '総務省／用語辞典', slag: 'mic-it-glossary' },
      {
        id: 2,
        name: '総務省／情報通信用語集',
        slag: 'mic-it-foreign-glossary',
      },
    ]
    const { route, $axios } = useContext()
    const glossaryId = computed(() => route.params.glossaryId)
    const pageName = ref('用語集一覧')
    const getTestData = async () => {
      await $axios.$get('http://localhost/api/test').then().catch()
    }
    return {
      pageName,
      glossaryId,
      glossariesData,
      getTestData,
    }
  },
})
</script>

<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center"> {{ pageName }} </v-card>
      <!-- 用語集一覧 -->
      <v-btn @click="getTestData()">get</v-btn>
      <v-card
        v-for="(glossary, index) in glossariesData"
        :key="index"
        :to="glossary.slag"
        nuxt
      >
        <v-card-title>{{ glossary.name }}</v-card-title>
      </v-card>
    </v-col>
  </v-row>
</template>
