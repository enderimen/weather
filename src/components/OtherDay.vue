<template>
  <footer class="o-status__list">
    <div
      class="o-status__item"
      v-for="weather in weatherList"
      :key="weather.day"
    >
      <CustomText class="o-status__date">{{ weather.date }}</CustomText>
      <CustomText class="o-status__day" :size="'small'">
        {{ weather.day }}
      </CustomText>

      <img
        class="o-status__img"
        :src="weather.image"
        :alt="weather.status"
        height="24"
      />

      <div class="o-status__info">
        <CustomText :size="'small'"
          >Sıcaklık: {{ weather.degree }}°
          <CustomText class="o-status__infoHumidity" :size="'small'"
            >Nem: {{ weather.humidity }}%
          </CustomText>
        </CustomText>
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
    background-color: rgba(0, 0, 0, 0.2);

    @media (--t) {
      flex-direction: row;
    }
  }

  &__item {
    color: var(--txt-color-light);
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    padding: 5px 20px;
    width: 100%;

    &:not(:last-child) {
      border-bottom: 0.5px solid #7a7180;

      @media (--t) {
        border-bottom: 0;
        border-right: 0.5px solid #7a7180;
      }
    }

    &:first-child {
      display: none;
    }

    &:last-child {
      margin-bottom: 10px;
    }

    @media (--t) {
      padding: 30px 20px;
      flex-direction: column;
      align-items: center;
    }
  }

  &__date {
    display: none;

    @media (--t) {
      display: inline-flex;
    }
  }

  &__day {
    @media (--t) {
      margin-bottom: 20px;
    }
  }

  &__img {
    display: none;

    @media (--t) {
      display: block;
      height: 24px;
      width: 24px;
      margin-bottom: 20px;
    }
  }

  &__info {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    text-align: center;

    @media (--t) {
      align-items: center;
      align-content: center;
    }

    &Humidity {
      display: none;

      @media (--t) {
        display: inline-flex;
        margin-bottom: 20px;
      }
    }
  }
}
</style>
