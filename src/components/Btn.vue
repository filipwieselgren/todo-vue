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
  background-color: rgb(128, 48, 48);
  color: antiquewhite;
}

.btn-done {
  background-color: green;
  color: antiquewhite;
}
</style>
