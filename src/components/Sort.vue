<template>
  <nav class="sort-container">
    <button @click="newItem" class="btn-padding btn-sort btn">
      Sort by newest todo
    </button>
    <button @click="oldItem" class="btn-padding btn-sort btn">
      Sort by oldest todo
    </button>
  </nav>
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
  border: 1px solid #333;
  border-radius: 5px;
}

.sort-container {
  margin-bottom: 30px;
}
</style>
