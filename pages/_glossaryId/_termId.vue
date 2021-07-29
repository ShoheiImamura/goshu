<script>
import {
  defineComponent,
  ref,
  computed,
  useContext,
} from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const { route } = useContext()
    // 用語集一覧データ
    const termCard = ref({
      id: 1,
      name: 'アーカイブ',
      slag: 'archive',
      englishName: 'archive',
      discription:
        '文書や記録などの対象となるウェブサイトを収集（しゅうしゅう）し、タイトルや公開者の情報をつけて組織（そしき）化し、ちく積保存（ほぞん）すること。',
      feature: '説明',
      examples: [
        { name: 'アーパネット', id: 2 },
        { name: 'アクセシビリティ', id: 3 },
        { name: '具体例3', id: 4 },
      ],
    })

    const referenceCard = ref({
      id: 2,
      name: 'アーパネット',
      slag: 'arpanet',
      englishName: 'ARPAnet',
      discription:
        'アメリカ国防総省（こくぼうそうしょう）高等研究計画局（ARPA：アーパ）が作成したコンピュータネットワーク。',
      feature: '今のインターネットの起源（きげん）と言われているネットワーク',
      examples: ['具体例1', '具体例2', '具体例3'],
    })

    const referencesData = [
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
    const glossaryId = computed(() => route.value.params.glossaryId)
    const termId = computed(() => route.value.params.termId)
    const pageName = ref('用語集一覧')

    const setReferenceCard = (termCardId) => {
      referenceCard.value = referencesData.find((data) => {
        return data.id === termCardId
      })
    }
    return {
      pageName,
      glossaryId,
      termId,
      termCard,
      referenceCard,
      setReferenceCard,
    }
  },
})
</script>
<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center"> 用語詳細 </v-card>
      <!-- 履歴カード -->
      <v-card outlined> </v-card>
      <!-- メインカード -->
      <v-card outlined
        ><v-card-subtitle> {{ termCard.name }}</v-card-subtitle>
        <v-card-text>
          <div>{{ termCard.discription }}</div>
          <v-divider></v-divider>
          <div
            v-for="(example, index) in termCard.examples"
            :key="index"
            @click="setReferenceCard(example.id)"
          >
            {{ example.name }}
          </div>
        </v-card-text>
      </v-card>
      <!-- 参照カード -->
      <v-card outlined
        ><v-card-subtitle> {{ referenceCard.name }}</v-card-subtitle>
        <v-card-text>
          <div>{{ referenceCard.discription }}</div>
          <v-divider></v-divider>
          <div v-for="(example, index) in referenceCard.examples" :key="index">
            {{ example }}
          </div>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
