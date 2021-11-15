<!--  -->
<template>
  <div>
    儿子{{value}}
    <button @click="change">点击修改</button>

  </div>
</template>

<script>
export default {
  data() {
    return {
    }
  },

  props: {
    value: {
      type: Number,
      default: 1
    }

  },
  created() {
    console.log('son created', '')
  },
  beforeMount() {
    console.log(' son beforeMount', '')
  },
  mounted() {
    console.log(' son mounted', '')
  },
  methods: {
    change() {
      this.$emit('update:val', 200)
    }
  }
}

</script>

<style lang='stylus' scoped></style>
