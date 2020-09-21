<template>
  <component class="a-customText" :is="tag" :class="size">
    <slot/>
  </component>
</template>

<script>
export default {
  name: 'CustomText',
  props: {
    tag: {
      type: String,
      default: 'b'
    },
    size: {
      type: String,
      default: 'normal', // normal:16, small:14, xl:32
      validator: function(value) {
        return ['normal', 'small', 'xl'].indexOf(value) !== -1
      }
    },
    position: {
      type: String,
      default: 'Center',
      required: false,
      validator: function (value){
        return ['Left', 'Center', 'Right'].indexOf(value) !== -1
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.a-customText {
  text-transform: capitalize;
}

.normal {
  font-size: inherit;
}
.small {
  font-size: 14px;
}
.xl{
  font-size: 32px;
}

.Left {
  text-align: left;
}

.Center {
  text-align: center;
}

.Right {
  text-align: right;
}

</style>