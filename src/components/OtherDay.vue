<template>
  <footer class="o-status__list">
    <div
      class="o-status__item"
      v-for="weather in weatherList"
      :key="weather.day"
    >
        <CustomText class="o-status__day" :size="'small'">
          {{ weather.day }}
        </CustomText>

        <div class="o-status__info">
          <CustomText :size="'small'">{{ weather.degree }}°</CustomText>
          <CustomText :size="'small'">{{ weather.description }}</CustomText>
        </div>
    </div>
  </footer>
</template>

<script>
import CustomText from "@/components/CustomText";
export default {
  name: "OtherDayList",
  components: { CustomText },
  props: {
    weatherList: Array
  }
};
</script>

<style lang="scss" scoped>


.o-status {

  &__list {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    background-color: rgba(0,0,0,.2);
  }

  &__item {
    color: var(--txt-color-gray);
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    padding: 5px 20px;
    width: 100%;

    &:not(:last-child) {
      border-bottom: 0.5px solid #7a7180;
    }

    &:first-child {
      display: none;
    }
  }

  &__info {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
}
</style>
