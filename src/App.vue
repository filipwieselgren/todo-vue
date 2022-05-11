<template>
  <HandleEvents />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HandleEvents from "./components/HandleEvents.vue";

@Options({
  components: {
    HandleEvents,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  margin-top: 10em;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn-padding {
  padding: 10px;
  margin: 5px;
}

.btn {
  border: none;
  border-radius: 5px;
}
</style>
