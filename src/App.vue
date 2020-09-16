<template>
  <Container>
    <section class="wrapper">
      <input
        class="a-location__input"
        type="text"
        placeholder="İl veya ilçe giriniz"
        v-model="location"
      />
      <Info />
      <div class="a-degree">
        19° {{location}}
      </div>

      <div class="a-weather__status">
        <CustomText size="xl">Güneşli</CustomText>
      </div>
    </section>
  </Container>
</template>

<script>
import Container from "@/components/Container";
import Info from "@/components/Info";
export default {
  name: "App",
  components: {
    Info,
    Container,
  },
  data() {
    return {
      location: ""
    };
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
  margin-top: calc(100% - 75%);
}
</style>
