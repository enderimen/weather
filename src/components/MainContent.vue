<template>
  <section class="main" :class="status">
    <slot/>
  </section>
</template>

<script>
export default {
  name: 'MainContent',
  props: {
    status: String,
    validator: function(value) {
      return ['Clear', 'Snow', 'Rain', 'Clouds'].indexOf(value) !== -1
    }
  }
}
</script>

<style scoped>
.Clear {
  background-image: url("../assets/sunny-m.jpg");

  @media (--t) {
    background-image: url("../assets/sunny-d.jpg");
  }
}

.Snow {
  background-image: url("../assets/chill-m.jpg");

  @media (--t) {
    background-image: url("../assets/chill-d.jpg");
  }
}

.Rain {
  background-image: url("../assets/rain.jpg");

  @media (--t) {
    background-image: url("../assets/rain-d.jpg");
  }
}

.Clouds {
  background-image: url("../assets/cloudly-m.jpg");

  @media (--t) {
    background-image: url("../assets/cloudly-d.jpg");
  }
}
</style>