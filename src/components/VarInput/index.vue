<template>
  <div class="var-input-wrap">
    <el-input v-model="data" class="w-100" :type="type" :resize="resize" :rows="rows" size="small" @focus="$eventBus.$emit('remove-keydown')" @input="onInput" @change="onChange"></el-input>
    <div>
      <el-tooltip effect="dark" placement="bottom-start" :open-delay="300">
        <div class="w-200p" style="line-height: 20px;" slot="content">输入框中输入'${key}其中key为变量的Key'，所有${key}的字段都将被认定为变量字符串，调用vue打印模板的print方法传入对应的变量属性Key与值即可</div>
      </el-tooltip>
    </div>
  </div>
</template>



<script>
export default {
  props: {
    value: {
      type: String,
      default: 'text'
    },
    type: {
      type: String,
      default: 'text'
    },
    rows: {
      type: Number,
      default: 4
    },
    resize: {
      type: String,
      default: 'none'
    }
  },
  data() {
    return {
      data: this.value
    }
  },
  watch: {
  },
  created() {
    // console.log(this.value)
  },
  methods: {
    onInput() {
      this.$emit('input', this.data)
    },
    onChange() {
      this.$store.dispatch('components/setComponentVariable')
      this.$emit('change', this.data)
    }
  }
}
</script>

<style lang="scss">

</style>
