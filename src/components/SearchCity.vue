<template>
  <header>
    <input
      class="a-location__input"
      type="text"
      placeholder="İl veya ilçe giriniz"
    />
  </header>
</template>

<script>
export default {
  name: "SearchCity"
};
</script>

<style lang="scss" scoped>
.a-location__input {
  height: 40px;
  padding-left: 15px;
  padding-right: 15px;
  border: 1px solid #cecaca;
  border-radius: 15px;
  box-shadow: 2px 3px 50px #696262;
  margin-top: 40px;
  width: 290px;
  max-width: 300px;
  text-align: center;
  outline: none;
}
</style>
