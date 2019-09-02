<template>
  <div>
    <app-header></app-header>
    <group-dnd-local></group-dnd-local>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import GroupDnDLocal from "./components/GroupDnDLocal.vue";

export default {
  components: {
    "app-header": Header,
    "app-footer": Footer,
    "group-dnd-local": GroupDnDLocal
  },
  data() {
    return {
      //data
    };
  }
};
</script>

<style lang="scss">
/* Scoped means this styling applies only for this component */
// $bg-color: rgb(54, 170, 228);
$bg-color: #2a3439;

div {
  background-color: $bg-color;
}

body {
  margin: 0;
}
</style>