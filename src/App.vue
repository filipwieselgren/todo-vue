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
  font-family: "Roboto", sans-serif;
  font-family: "Space Mono", monospace;
}

body {
  background-color: rgb(163, 210, 249);
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
  border-radius: 5px;
  background-color: rgba(255, 255, 255, 0);
  border: 1px solid #333;
  box-shadow: 3px 3px 1px 1px #494949;
}

.btn:hover {
  cursor: pointer;
  box-shadow: -3px -3px 1px 1px #494949;
}
</style>
