<template>
  <div class="card-left" v-if="commentsList.length == 0">
    <p>
      <button class="btn yellow w-100" v-on:click="$emit('loadComments')" >Загрузить комментарии</button>
    </p>
  </div>
  <div class="card" v-else>
    <h2>Комментарии</h2>
    <ul class="list" v-for="comment in commentsList" v-bind:key="comment.id">
      <li class="list-item">
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "uploadComments",
  emits:['loadComments'],
  props: ['commentsList'],
  data() {
    return {

    }
  }

}
</script>

<style scoped>

</style>
