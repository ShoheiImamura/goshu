<script>
import { defineComponent, ref, computed } from '@vue/composition-api'

export default defineComponent({
  setup(_, context) {
    // 用語集一覧データ
    const glossariesData = [
      { id: 1, name: '総務省／用語辞典', slag: 'mic-it-glossary' },
      {
        id: 2,
        name: '総務省／情報通信用語集',
        slag: 'mic-it-foreign-glossary',
      },
    ]
    const glossaryId = computed(() => context.root.$route.params.glossaryId)
    const pageName = ref('用語集一覧')
    return {
      pageName,
      glossaryId,
      glossariesData,
    }
  },
})
</script>

<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center"> {{ pageName }} </v-card>
      <!-- 用語集一覧 -->
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
