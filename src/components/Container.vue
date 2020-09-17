<template>
  <div class="container">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Container'
}
</script>

<style lang="scss" scoped>
.container {
  margin-left: auto;
  margin-right: auto;
  background-image: url("../assets/chill2.png");
  background-size: cover;
  height: 100vh;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}
</style>