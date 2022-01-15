<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select v-model="type" id="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="value" id="value" rows="3"></textarea>
    </div>

    <button class="btn" :disabled="isValid">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: ['add-block'],
  data () {
    return {
      type: 'title',
      value: ''
    }
  },
  computed: {
    isValid () {
      return this.value.length < 4
    }
  },
  methods: {
    submit () {
      this.$emit('add-block', {
        type: this.type,
        value: this.value,
        id: Date.now()
      })
      this.type = 'title'
      this.value = ''
    }
  }
}
</script>
