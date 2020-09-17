<template>
  <section class="main">
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
  background-image: url("../assets/sunny.jpg");
}

.Snow {
  background-image: url("../assets/chill2.png");
}

.Rain {
  background-image: url("../assets/sunny3.jpg");
}

.Clouds {
  background-image: url("../assets/chill.png");
}
</style>