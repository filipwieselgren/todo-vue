<template>
  <div class="form-con">
    <form @submit.prevent="handleSubmit" class="form">
      <input
        type="text"
        v-model="item"
        placeholder="Add todo"
        class="input btn-padding"
      />
      <button
        type="button"
        @click="handleSubmit"
        class="btn btn-padding btn-submit"
      >
        Submit
      </button>
    </form>
  </div>
  <div v-if="novalue" class="error">
    <div>{{ error }}</div>
  </div>
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
    const newId: number = this.id++;

    const newDate: any = Date.now();

    if (this.item) {
      this.item;
      this.$emit("addItem", new Item(this.item, newId, this.done, newDate));
      this.item = "";
      this.novalue = false;
    } else {
      this.novalue = true;
      this.error =
        "Du har missat att skriva en todo. Kanske en todo kan vara att skriva en? 😉";
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
  background-color: rgba(255, 255, 255, 0);
  width: 80%;
}

.input::placeholder {
  color: #333;
}

.error > div {
  text-align: center;
  color: #333;
}

.btn-submit {
  box-shadow: 3px 3px 1px 1px #494949;
  color: #333;
}
</style>
