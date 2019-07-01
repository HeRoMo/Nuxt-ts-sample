<template lang="pug">
div
  section
    h1 FILE: {{fileName}}
    ul
      li ROUTE NAME: {{JSON.stringify($route.name)}}
      li PATH: {{JSON.stringify($route.path)}}
      li PARAMS: {{JSON.stringify($route.params)}}
    nuxt-child
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'nuxt-property-decorator'

const FILE_NAME = 'pages/groups/index.vue'

@Component
class GroupIndex extends Vue {
  @Prop({ default: FILE_NAME }) fileName!: string

  asyncData() {
    console.log(`asyncData IN ${FILE_NAME}`)
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
export default GroupIndex
</script>

<style lang="sass" scoped>
section
  border: solid 1px orange
  background-color: #FF8856
  padding: 3px
</style>
