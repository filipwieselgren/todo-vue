<template>
  <div>
    <button @click="newItem">Sort by newest todo</button>
    <button @click="oldItem">Sort by oldest todo</button>
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

<style scoped lang="scss"></style>
