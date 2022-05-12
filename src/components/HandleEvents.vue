<template>
  <Sort @handleNewItem="sortNewItem()" @handleOldItem="sortOldItem()" />
  <div class="main-container">
    <AddItems @addItem="handleAddItem($event)" />
    <div class="list-con">
      <div
        v-for="item in items"
        :key="item.id"
        :class="['list', { listDone: item.done }]"
      >
        <div class="list-item">{{ item.item }}</div>

        <div class="btn-con">
          <Btn
            :itemlist="item.id"
            @removeItem="remove($event)"
            @doneItem="done($event)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

import AddItems from "./AddItems.vue";
import { Item } from "@/models/Item";
import Btn from "./Btn.vue";
import Sort from "./Sort.vue";

@Options({
  components: {
    AddItems,
    Btn,
    Sort,
  },
})
export default class HandleEvents extends Vue {
  items: Item[] = [];
  isDone = false;

  handleAddItem(it: Item) {
    this.items.push(it);

    localStorage.setItem("item", JSON.stringify(this.items));
  }

  remove(ri: number) {
    this.items = this.items.filter((item) => {
      return item.id !== ri;
    });

    localStorage.setItem("item", JSON.stringify(this.items));
  }

  done(ri: number) {
    this.items.forEach((item) => {
      if (item.id === ri && this.isDone === false) {
        item.done = this.isDone = true;
        localStorage.setItem("item", JSON.stringify(this.items));
      } else if (item.id === ri && this.isDone === true) {
        item.done = this.isDone = false;
        localStorage.setItem("item", JSON.stringify(this.items));
      } else {
        return;
      }
    });
  }

  sortNewItem() {
    this.items.sort((todoA, todoB) => todoB.date - todoA.date);

    this.items.map((item) => item.item);

    localStorage.setItem("item", JSON.stringify(this.items));
  }

  sortOldItem() {
    this.items.sort((todoA, todoB) => todoA.date - todoB.date);

    this.items.map((item) => item.item);

    localStorage.setItem("item", JSON.stringify(this.items));
  }

  mounted() {
    if (localStorage.getItem("item") != null) {
      this.items = JSON.parse(localStorage.getItem("item") || "[]");
    } else {
      return;
    }
  }
}
</script>

<style scoped lang="scss">
.main-container {
  width: 80%;
}

.list-con {
  max-height: 50vh;
  overflow: scroll;
}

.list {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  border-bottom: 1px solid #333;
  margin-bottom: 10px;
  .list-item {
    max-width: 50%;
    min-width: 33%;
    overflow: auto;
  }
}

.listDone {
  text-decoration: line-through;
  color: green;
  position: relative;
}

@media only screen and (min-width: 768px) {
  .main-container {
    width: 50%;
  }
}

@media only screen and (min-width: 1024px) {
  .main-container {
    width: 33%;
  }
}
</style>
