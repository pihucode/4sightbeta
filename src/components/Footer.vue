<template>
  <footer>
    <p>{{ copyright }}</p>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      copyright: "2019. 4sightbeta"
    };
  }
};
</script>

<style scoped>
footer {
  background: #222;
  padding: 6px;
}

p {
  color: mediumturquoise;
  text-align: center;
}
</style>
