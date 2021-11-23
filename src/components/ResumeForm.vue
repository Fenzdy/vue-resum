<template>
  <div class="card card-left">
    <form v-on:submit.prevent="submit">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" v-model="value" rows="3"></textarea>
      </div>

      <button class="btn yellow w-100" v-bind:disabled="!isValid">Добавить</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ResumeForm',
  emits: ['submitForm'],
  data(){
    return {
      type: 'title',
      value: '',
    }
  },

  methods: {
    submit() {
      this.$emit('submitForm', {
        type: this.type,
        value: this.value,
        id: Date.now()
      })
      this.value = ''
    }
  },
  computed: {
    isValid(){
      return this.value.length > 3
    },
  },

}
</script>

<style scoped>

</style>
