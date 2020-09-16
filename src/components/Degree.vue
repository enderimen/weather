<template>
  <div class="a-degree">
      19°
  </div>
</template>

<script>
export default {
  name: 'Degree'
}
</script>

<style lang="scss" scoped>

.a-degree {
  font-size: 6rem;
  font-weight: 300;
  text-shadow: 3px 8px 9px var(--txt-shadow-color);
  margin-top: calc(100% - 75%);
}

</style>