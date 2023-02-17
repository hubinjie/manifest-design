<template>
  <div :id="elementId" class="receiver-address-component">
    <span class="detail" :style="getTextStyle">{{ getText }}</span>
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
      },
      addressType: {
        type: String,
        default: 'ssqjm',
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
      },
      getText() {
        const { addressType } = this;
        return addressType==='ssqjm'?'中国广东省深圳市龙岗区江南时代大厦303B,518000':'Room 303B, Jiangnan Times Building, Longgang District, Shenzhen, China, 518000'
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
  .receiver-address-component {
    .detail {
      display: inline-block;
      font-weight: normal;
      word-break: break-all;
      word-wrap: break-word;
      border: 1px solid transparent;
    }
  }
</style>
