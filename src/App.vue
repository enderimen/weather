<template>
  <MainContent :class="weatherList.length > 0 ? weatherList[0].status : ''">
    <Container>
      <div class="v-flex">
        <!-- search location -->
        <header class="wrapper">
          <input
            class="a-location__input"
            type="text"
            placeholder="İl veya ilçe giriniz"
            v-model="location"
            @keypress.enter="fetchWeather"
          />
        </header>

        <!-- location weather information -->
        <main class="o-content">
          <Info :city="city" :weather-list-length="weatherList.length" />

          <div class="a-degree">
            {{ `${weatherList.length > 0 ? weatherList[0].degree : "0"}°` }}
          </div>
          <div class="a-weather__status">
            <CustomText :tag="'p'" :size="'xl'">{{
              weatherList.length > 0 ? weatherList[0].description : ""
            }}</CustomText>
            <div class="a-weather__info">
              <CustomText :size="'small'"
                >Nem:
                {{
                  `${weatherList.length > 0 ? weatherList[0].humidity : "0"}%`
                }}</CustomText
              >
              <CustomText :size="'small'">
                | Gece:
                {{
                  `${weatherList.length > 0 ? weatherList[0].night : "0"}°`
                }}</CustomText
              >
            </div>
          </div>
        </main>

        <!-- other day weather information -->
        <OtherDayList :weatherList="weatherList" />
      </div>
    </Container>
  </MainContent>
</template>

<script>
import Container from "@/components/Container";
import Info from "@/components/Info";
import CustomText from "@/components/CustomText";
import OtherDayList from "@/components/OtherDay";
import MainContent from "@/components/MainContent";

export default {
  name: "App",
  components: {
    MainContent,
    OtherDayList,
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
      weatherStatus: ["Rain", "Snow", "Clear"],
      weatherList: [],
      city: ""
    };
  },
  created() {
    this.fetchWeather();
  },
  methods: {
    fetchWeather() {
      this.location = this.location == "" ? "İstanbul" : this.location;
      fetch(this.apiUrl + this.location, {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
          Authorization: this.apiKey
        }
      }).then(response => {
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
          date: weather.date,
          day: weather.day,
          degree: parseInt(weather.degree),
          humidity: parseInt(weather.humidity),
          description:
            weather.description == "açık" ? "Güneşli" : weather.description,
          max: parseInt(weather.max),
          min: parseInt(weather.min),
          night: parseInt(weather.night),
          status: weather.status,
          image: weather.icon
        });
      });
    }
  }
};
</script>

<style lang="scss">
.main {
  background-image: url("assets/chill-m.jpg");

  @media (--t) {
    background-image: url("./assets/404.jpg");
  }

  transition: background 0.5s;
  background-size: cover;
  color: var(--txt-color-light);
  height: 100vh;
  overflow-y: auto;
}

.o-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 50px;
}

.v-flex {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: calc(100% - 20px);
}

.h-flex {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

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

.a-weather {
  &__status {
    font-weight: 600;
    text-shadow: 3px 8px 9px var(--txt-shadow-color);
    text-align: center;
  }

  &__info {
    margin-top: 20px;
  }
}

.a-degree {
  font-size: 6rem;
  font-weight: 300;
  text-shadow: 3px 8px 9px var(--txt-shadow-color);
  margin-top: calc(100% - 95%);
}
</style>
