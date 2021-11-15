<!--  -->
<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    model: {
      type: Object,
      required: true
    },
    rules: {
      type: Object
    }
  },
  provide() {
    return {
      form: this //传递form实例给子代
    }
  },
  data() {
    return {
    }
  },
  methods: {
    validate(cb) {
      //map结果是若干Promise数组
      console.log('this.$children', this.$children)
      const tasks = this.$children.filter(item => item.prop).map(item => item.validate());
      console.log('tasks', tasks)
      Promise.all(tasks)
        .then(() => { cb(true) })
        .catch(() => { cb(false) });

    }
  }
}

</script>

<style lang='stylus' scoped></style>
