<template>
  <div :id="elementId" class="receiver-name-component">
    <span class="detail" :style="getTextStyle">Alex Hu</span>
  </div>
</template>

<script>
  export default {
    props: {
      elementId: {
        type: String,
        default: '',
      },
      text: {
        type: String,
        default: '',
      },
      fontFamily: {
        type: String,
        default: '',
      },
      fontSize: {
        type: String,
        default: '',
      },
      lineHeight: {
        type: String,
        default: '',
      },
      isBold: {
        type: Boolean,
        default: false,
      },
      hasBorder: {
        type: Boolean,
        default: false,
      }
    },
    data() {
      return {
      };
    },
    computed: {
      getTextStyle() {
        const { fontFamily, fontSize, lineHeight, isBold, hasBorder } = this;
        let style = {};
        style = {
          fontFamily,
          fontSize,
          lineHeight,
          fontWeight: isBold ? 'bold' : '400',
          border: hasBorder ? '1px solid #000' : '1px solid transparent',
        };
        return style;
      }
    },
    mounted() {
      this.init();
    },
    methods: {
      init() {
        this.$emit('complete');
      },
    },
  };
</script>

<style lang="scss">
  .receiver-name-component {
    .detail {
      display: inline-block;
      font-weight: normal;
      word-break: break-all;
      word-wrap: break-word;
      border: 1px solid transparent;
    }
  }
</style>
