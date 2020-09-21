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
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  height: 100%;
}
</style>