<template>
  <section class="m-info">
    <CustomText :tag="'h3'" class="m-info__location">İstanbul, Türkiye</CustomText>
    <CustomText :tag="'p'" class="m-info__date">{{ getFullYear() }}</CustomText>
  </section>
</template>

<script>
import CustomText from "@/components/CustomText";
export default {
  name: "Info",
  components: { CustomText },
  data() {
    return {
      days: [
        "Pazartesi",
        "Salı",
        "Çarşamba",
        "Perşembe",
        "Cuma",
        "Cumartesi",
        "Pazar"
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
      return this.days[this.date.getDay() - 1];
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
    getFullYear() {
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
  }

  &__date {
    font-style: italic;
    font-size: 1rem;
  }
}
</style>
