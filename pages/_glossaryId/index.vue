<script>
import { computed, defineComponent, useContext } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const { route } = useContext()
    // 用語集（用語一覧）データ
    const termCards = [
      {
        id: 1,
        name: 'アーカイブ',
        slag: 'archive',
        englishName: 'archive',
        discription:
          '文書や記録などの対象となるウェブサイトを収集（しゅうしゅう）し、タイトルや公開者の情報をつけて組織（そしき）化し、ちく積保存（ほぞん）すること。',
        feature: '説明',
        examples: ['具体例1', '具体例2', '具体例3'],
      },
      {
        id: 2,
        name: 'アーパネット',
        slag: 'arpanet',
        englishName: 'ARPAnet',
        discription:
          'アメリカ国防総省（こくぼうそうしょう）高等研究計画局（ARPA：アーパ）が作成したコンピュータネットワーク。',
        feature: '今のインターネットの起源（きげん）と言われているネットワーク',
        examples: ['具体例1', '具体例2', '具体例3'],
      },
      {
        id: 3,
        name: 'アクセシビリティ',
        slag: 'accesibility',
        englishName: 'accesibility',
        discription:
          '情報（じょうほう）やサービス、ソフトウェアなどが、どのくらい、広いはん囲の人たちに利用可能（かのう）であるかを表す言葉。',
        feature:
          '高れい者や障（しょう）がい者などハンディを持つ人にとって、どのくらい利用しやすいかということを意味する。',
        examples: ['具体例1', '具体例2', '具体例3'],
      },
    ]

    const glossaryId = computed(() => route.params.glossaryId)
    return { glossaryId, termCards }
  },
})
</script>


<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        用語集詳細（用語一覧）
      </v-card>
      <!-- 用語一覧 -->
      <v-card
        v-for="(termCard, index) in termCards"
        :key="index"
        :to="glossaryId + '/' + termCard.slag"
        nuxt
      >
        <v-card-title>{{ termCard.name }}</v-card-title>
      </v-card>
    </v-col>
  </v-row>
</template>
