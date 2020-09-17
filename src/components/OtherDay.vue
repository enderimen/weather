<template>
  <div class="o-status__item">
    <CustomText class="o-status__day">
      Perşembe
    </CustomText>

    <div class="o-status__info">
      <CustomText>17°</CustomText>
      <CustomText>Yağmurlu</CustomText>
    </div>
  </div>
</template>

<script>
import CustomText from "@/components/CustomText";
export default {
  components: { CustomText }
};
</script>

<style lang="scss" scoped>
.o-status {
  &__item {
    color: var(--txt-color-gray);
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    padding: 10px;
    width: 100%;
    &:not(:last-child) {
      border-bottom: .5px solid #423549;
    }
  }

  &__info {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
}
</style>
