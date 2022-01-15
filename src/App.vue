<template>
  <div class="container column">
    <ResumeForm @add-block="addBlock" />
    <ResumeView :blocks="blocks" />
  </div>
  <div class="container">
    <ResumeLoader v-if="loading" />
    <ResumeComments
      v-else
      @load-comments="loadComments"
      :comments="comments"
    />
  </div>
</template>

<script>
import ResumeForm from './components/ResumeForm'
import ResumeView from './components/ResumeView'
import ResumeLoader from './components/ResumeLoader'
import ResumeComments from './components/ResumeComments'

export default {
  data () {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    addBlock (block) {
      this.blocks.push(block)
    },
    async loadComments () {
      this.loading = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=13')
      this.comments = await res.json()
      this.loading = false
    }
  },
  components: {
    ResumeForm,
    ResumeView,
    ResumeLoader,
    ResumeComments
  }
}
</script>
