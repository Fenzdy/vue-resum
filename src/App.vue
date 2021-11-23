<template>
  <div class="container column">
    <ResumeForm v-on:submitForm="addInfo"></ResumeForm>
    <ResumeView v-bind:blockResume="blockResume" v-on:cleanResume="cleanResume"></ResumeView>
  </div>
  <div class="container">
    <UploadComments
      v-on:loadComments="loadComments"
      v-bind:commentsList="comments"
    ></UploadComments>
    <AppLoader v-if="load"></AppLoader>
  </div>
</template>

<script>
import ResumeForm from "./components/ResumeForm";
import ResumeView from "./components/ResumeView";
import UploadComments from "./components/UploadComments";
import AppLoader from "./components/AppLoader";

export default {
  data(){
    return {
      comments: [],
      load: false,
      blockResume: [],
    }
  },
  mounted() {
    // this.loadComments()
  },
  methods: {
    async loadComments() {
      this.load = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await res.json()
      this.load = false
    },
    addInfo(block){
      this.blockResume.push(block)
    },
    cleanResume(){
      this.blockResume = []
    },
  },
  components: {
    ResumeForm,
    ResumeView,
    UploadComments,
    AppLoader,
  }
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
