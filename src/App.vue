<template>
  <Container>
    <section class="wrapper">
      <SearchCity />
      <Info />
      <Degree/>

      <WeatherStatus/>
    </section>
  </Container>
</template>

<script>
import SearchCity from "@/components/SearchCity";
import Container from "@/components/Container";
import Info from "@/components/Info";
import Degree from "@/components/Degree";
import WeatherStatus from "@/components/WeatherStatus";
export default {
  name: "App",
  components: {
    WeatherStatus,
    Degree,
    Info,
    Container,
    SearchCity
  }
};
</script>

<style lang="scss">
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  background-image: url("./assets/chill.png");
  background-size: cover;
  height: 100vh;
  color: #fff;
}
</style>
