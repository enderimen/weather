<template>
  <section class="m-info">
    <CustomText :tag="'h3'" class="m-info__location">{{ weatherListLength > 0 ? city : "Konum Bulunamadı!" }}</CustomText>
    <CustomText :tag="'p'" class="m-info__date">{{ getFullDate() }}</CustomText>
  </section>
</template>

<script>
import CustomText from "@/components/CustomText";
export default {
  name: "Info",
  components: { CustomText },
  props: {
    city: String,
    weatherListLength: Number
  },
  data() {
    return {
      days: [
        "Pazar",
        "Pazartesi",
        "Salı",
        "Çarşamba",
        "Perşembe",
        "Cuma",
        "Cumartesi"
      ],
      months: [
        "Ocak",
        "Şubat",
        "Mart",
        "Nisan",
        "Mayıs",
        "Haziran",
        "Temmuz",
        "Ağustos",
        "Eylül",
        "Ekim",
        "Kasım",
        "Aralık"
      ],
      date: new Date()
    };
  },
  computed: {
    getDay() {
      return this.days[this.date.getDay()];
    },
    getMonth() {
      return this.months[this.date.getMonth()];
    },
    getYear() {
      return this.date.getFullYear();
    },
    getDate() {
      return this.date.getDate();
    }
  },
  methods: {
    getFullDate() {
      return `${this.getDate} ${this.getMonth} ${this.getYear} ${this.getDay}`;
    }
  }
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
    text-transform: capitalize;
  }

  &__date {
    font-style: italic;
    font-size: 1rem;
  }
}
</style>
