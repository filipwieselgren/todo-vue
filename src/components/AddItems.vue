<template>
  <div class="form-con">
    <form @submit.prevent="handleSubmit" class="form">
      <input
        type="text"
        v-model="item"
        placeholder="Add todo"
        class="input btn-padding"
      />
      <button type="button" @click="handleSubmit" class="btn btn-padding">
        Submit
      </button>
    </form>
  </div>
  <div v-if="novalue" class="error">{{ error }}</div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Item } from "@/models/Item";
export default class AddItems extends Vue {
  item = "";
  error!: string;
  id = 0;
  done = false;
  date = 0;
  novalue = false;
  items: Item[] = [];

  handleSubmit() {
    const newId: any = Math.random();
    const newDate: number = Date.now();

    if (this.item) {
      this.item;
      this.$emit("addItem", new Item(this.item, newId, this.done, newDate));
      this.item = "";
      this.novalue = false;
    } else {
      this.novalue = true;
      this.error = "Inget värde";
    }
  }
}
</script>

<style scoped lang="scss">
.form-con {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}
.form {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.input {
  border: none;
  border-bottom: 1px solid #333;
  margin: none;
}

.error {
  width: 100%;
  text-align: center;
}
</style>
