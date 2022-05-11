<template>
  <div>
    <button @click="newItem" class="btn-padding btn-sort">
      Sort by newest todo
    </button>
    <button @click="oldItem" class="btn-padding btn-sort">
      Sort by oldest todo
    </button>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class Sort extends Vue {
  newItem() {
    this.$emit("handleNewItem");
  }

  oldItem() {
    this.$emit("handleOldItem");
  }
}
</script>

<style scoped lang="scss">
.btn-sort {
  border: none;
  border-radius: 5px;
}
</style>
