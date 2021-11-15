<!--  -->
<template>
  <div><input
      :value=value
      @input="onInput($event)"
      v-bind="$attrs"
    > </div>

</template>

<script>
export default {
  inheritAttrs: false,
  data() {
    return {
    }
  },
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  methods: {
    onInput(e) {
      this.$emit('input', e.target.value);
      // 通知FormItem进行校验
      this.$parent.$emit('validate')
    }
  }
}

</script>

<style lang='stylus' scoped></style>
