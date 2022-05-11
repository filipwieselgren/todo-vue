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
    console.log("klickat på handleRemove i Btn", this.itemlist);

    this.$emit("removeItem", this.itemlist);
  }

  handleDone() {
    console.log("klickat på handleDone i Btn", this.itemlist);

    this.$emit("doneItem", this.itemlist);
  }
}
</script>

<style scoped lang="scss">
.btn-con {
  display: flex;
}
</style>
