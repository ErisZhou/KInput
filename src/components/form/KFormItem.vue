<!--  -->
<template>
  <div>
    <label v-if="label">{{label}}</label>
    <slot></slot>
    <!-- 校验信息 -->
    <p v-if="errorMessage">{{errorMessage}}</p>

  </div>
</template>

<script>
import Schema from 'async-validator'
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    prop: String

  },
  inject: ['form'],
  data() {
    return {
      errorMessage: ''
    }
  },
  mounted() {
    //监听校验事件并执行监听
    this.$on("validate", () => {
      this.validate()
    })
  },
  methods: {
    validate() {
      //执行组件校验
      //1.获取校验规则
      const rules = this.form.rules[this.prop];
      //2.获取数据
      const value = this.form.model[this.prop];
      //执行校验
      const desc = { [this.prop]: rules }
      const schema = new Schema(desc);
      //除了同步校验外还有可能有异步校验
      //返回的Promise<boolean>
      return schema.validate({ [this.prop]: value }, errors => {
        if (errors) {
          this.errorMessage = errors[0].message;
        }
        else {
          this.errorMessage = '';
        }
      }); //参数1 是值,参数2是校验错误对象数组

    }
  }

}

</script>

<style  scoped></style>
