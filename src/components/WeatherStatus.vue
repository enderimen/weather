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

<style scoped>
</style>