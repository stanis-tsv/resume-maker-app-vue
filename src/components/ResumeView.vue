<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'resume-' + block.type"
        v-bind="{value: block.value}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from './blocks/ResumeTitle'
import ResumeSubtitle from './blocks/ResumeSubtitle'
import ResumeAvatar from './blocks/ResumeAvatar'
import ResumeText from './blocks/ResumeText'

export default {
  props: ['blocks'],
  components: {
    ResumeTitle,
    ResumeSubtitle,
    ResumeAvatar,
    ResumeText
  }
}
</script>
