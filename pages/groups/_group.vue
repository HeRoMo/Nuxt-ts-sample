<template lang="pug">
div
  section(v-if="isMtachName")
    h1 FILE: {{fileName}}
    ul
      li ROUTE NAME: {{JSON.stringify($route.name)}}
      li PATH: {{JSON.stringify($route.path)}}
      li PARAMS: {{JSON.stringify($route.params)}}
  nuxt-child
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'nuxt-property-decorator'

const FILE_NAME = 'pages/groups/_group.vue'

@Component
class Group extends Vue {
  @Prop({ default: FILE_NAME }) fileName!: string

  get isMtachName(): boolean {
    return this.$route.name === 'groups-group'
  }

  asyncData({ route }) {
    console.log(`asyncData IN ${FILE_NAME}`)
    // 親・子どちらへのアクセスでも実行したい処理

    if (route.name !== 'groups-group') return

    // 親コンポーネントのパスへのアクセス時のみ実行したい処理
  }

  async fetch() {
    console.log(`fetch IN ${FILE_NAME}`)
  }

  validate(arg) {
    console.log(`validate IN ${FILE_NAME}`)
    return true
  }

  beforeCreate() {
    console.log(`beforeCreate IN ${FILE_NAME}`)
  }

  created() {
    console.log(`created IN ${this.fileName}`)
  }

  beforeMount() {
    console.log(`beforeMount IN ${this.fileName}`)
  }

  mounted() {
    console.log(`mounted IN ${this.fileName}`)
  }
}
export default Group
</script>

<style lang="sass" scoped>
section
  border: solid 1px yellow
  background-color: #FFFF88
  padding: 3px
</style>
