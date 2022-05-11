<template>
  <button @click="handleRemove" class="btn btn-padding">Remove</button>
  <button @click="handleDone" class="btn btn-padding">Done</button>
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
</style>
