<template>
  <div class="a-weather__status">
    <CustomText size="xl">Güneşli</CustomText>
  </div>
</template>

<script>
import CustomText from "@/components/CustomText";
export default {
  name: 'WeatherStatus',
  components: {CustomText}
}
</script>

<style lang="scss" scoped>
.a-weather__status {
  font-weight: 600;
  text-shadow: 3px 8px 9px var(--txt-shadow-color);
}
</style>