<template>
  <header>
    <!-- <div class="title-div"> -->
    <h1 class="title">4sight</h1>
    <h2 class="superscript">beta</h2>
    <!-- </div> -->
    <p>
      In the future, a feature to save schedules will be added.
      For now, please take screenshots!
    </p>
  </header>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style scoped lang="scss">
$header-bg: #373549;
$h1-color: whitesmoke;

header {
  background: $header-bg;
  padding-top: 42px;
  text-align: center;
}

.title {
  color: $h1-color;
  display: inline;
}

.superscript {
  font-size: 12px;
  display: inline;
}

p {
  padding-top: 32px;
}
</style>
