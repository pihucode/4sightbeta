<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  data() {
    return {
      title: "4sightbeta"
    };
  }
};
</script>

<style scoped lang="scss">
$header-bg: #373549;
$h1-color: whitesmoke;

header {
  background: $header-bg;
  padding: 10px;
}

h1 {
  color: $h1-color;
  text-align: center;
}
</style>
