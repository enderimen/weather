<template>
  <section class="m-info">
    <CustomText :tag="'h3'" class="m-info__location"
      >İstanbul, Türkiye</CustomText
    >
    <CustomText :tag="'p'" class="m-info__date"
      >16 Eylül 2020 Çarşamba</CustomText
    >
  </section>
</template>

<script>
import CustomText from "@/components/CustomText";
export default {
  name: "Info",
  components: { CustomText }
};
</script>

<style lang="scss" scoped>
.m-info {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  &__location {
    margin-bottom: 20px;
    font-size: 2rem;
  }

  &__date {
    font-style: italic;
    font-size: 1rem;
  }
}
</style>
