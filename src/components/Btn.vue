<template>
  <button @click="handleDone" class="btn btn-done btn-padding">Done</button>
  <button @click="handleRemove" class="btn btn-remove btn-padding">
    Remove
  </button>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class Btn extends Vue {
  @Prop() itemlist!: number;

  handleRemove() {
    this.$emit("removeItem", this.itemlist);
  }

  handleDone() {
    this.$emit("doneItem", this.itemlist);
  }
}
</script>

<style scoped lang="scss">
.btn-con {
  display: flex;
}

.btn-remove {
  background-color: rgba(255, 0, 0, 0.186);
}
.btn-done {
  background-color: green;
}
</style>
