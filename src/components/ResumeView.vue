<template>
  <div class="card card-right card-view">
    <template v-if="blockResume.length">
      <div class="card-view-clean" title="Очистить резюме"
        v-on:click="$emit('cleanResume')"
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 22 22" fill="none">
          <path fill-rule="evenodd" clip-rule="evenodd" d="M12.4141 10.9999L21.1123 2.30166L19.6981 0.887451L10.9999 9.5857L2.30166 0.887493L0.887451 2.30171L9.58566 10.9999L0.887451 19.6981L2.30166 21.1123L10.9999 12.4141L19.6981 21.1124L21.1123 19.6982L12.4141 10.9999Z" fill="#000"></path>
        </svg>
      </div>

      <component
        v-for="block in blockResume"
        v-bind:key="block.id"
        v-bind:is="'block-' + block.type"
        v-bind="{ value: block.value }"
      ></component>

    </template>
    <div v-else>
      <h1>Создай резюме мечты</h1>
    </div>
  </div>
</template>

<script>
import BlockTitle from "./resume_block/BlockTitle";
import BlockSubtitle from "./resume_block/BlockSubtitle";
import BlockAvatar from "./resume_block/BlockAvatar";
import BlockText from "./resume_block/BlockText";

export default {
  name: 'ResumeView',
  props: ['blockResume'],
  emits: ['cleanResume'],
  components: {
    BlockTitle,
    BlockSubtitle,
    BlockAvatar,
    BlockText,
  }

}
</script>

<style scoped>
  .card-view {
    position: relative;
  }
  .card-view-clean {
    position: absolute;
    right: 15px;
    top: 15px;
    cursor: pointer;
  }
</style>
