<template>
  <Container>
    <header class="wrapper">
      <input
        class="a-location__input"
        type="text"
        placeholder="İl veya ilçe giriniz"
        v-model="location"
        @keypress.enter="fetchWeather"
      />
      <Info :city="city" />
      <div class="a-degree">{{ weatherList.length > 0 ? weatherList[0].degree : "" }}°</div>
      <div class="a-weather__status">
        <CustomText :size="'xl'">{{ weatherList.length > 0 ? weatherList[0].description : "" }}</CustomText>
      </div>
    </header>

    <footer class="o-status__list">
      <OtherDay/>
      <OtherDay/>
      <OtherDay/>
    </footer>
  </Container>
</template>

<script>
import Container from "@/components/Container";
import Info from "@/components/Info";
import CustomText from "@/components/CustomText";
import OtherDay from "@/components/OtherDay";

export default {
  name: "App",
  components: {
    OtherDay,
    Info,
    Container,
    CustomText
  },
  data() {
    return {
      apiKey: "apikey 4NVazvZ7iHVZPecCO9106Y:0K052LPX0mgKnWiC0Y5UY4",
      apiUrl:
        "https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=",
      location: "İstanbul",
      weatherList: [],
      city: ""
    };
  },
  created() {
    this.fetchWeather();
  },
  methods: {
    fetchWeather() {
      fetch(this.apiUrl + this.location, {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
          Authorization: this.apiKey
        }
      })
        .then(response => {
          response.json().then(data => {
            this.city = data.city;
            this.clearAllWeatherField(data.result);
          });
        })
        .catch(() => {
          console.log("Bağlantı kurulurken sorun oluştu!");
        });
    },
    clearAllWeatherField(weatherList) {
      this.weatherList = [];

      weatherList.map(weather => {
        this.weatherList.push({
          degree: parseInt(weather.degree),
          humidity: parseInt(weather.humidity),
          description: weather.description,
          max: parseInt(weather.max),
          min: parseInt(weather.min),
          night: parseInt(weather.night),
          status: weather.status,
          image: weather.icon
        });
      });

      console.log(this.weatherList);
    }
  }
};
</script>

<style lang="scss">
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  color: var(--txt-color-light);
}

.a-location__input {
  height: 40px;
  padding-left: 15px;
  padding-right: 15px;
  border: 1px solid var(--border-color);
  border-radius: 15px;
  box-shadow: 2px 3px 20px var(--box-shadow);
  margin-top: 40px;
  width: 290px;
  max-width: 300px;
  text-align: center;
  outline: none;
}

.a-weather__status {
  font-weight: 600;
  text-shadow: 3px 8px 9px var(--txt-shadow-color);
}

.a-degree {
  font-size: 6rem;
  font-weight: 300;
  text-shadow: 3px 8px 9px var(--txt-shadow-color);
  margin-top: calc(100% - 95%);
}

.o-status__list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  background-color: red;
}
</style>
