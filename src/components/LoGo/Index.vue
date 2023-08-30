<template>
  <div :id="elementId" class="logo" >
    <img :src="src" class="image" >
  </div>
</template>
  
  <script>
export default {
  props: {
    elementId: {
      type: String,
      default: '',
    },
    src: {
      type: String,
      default: 'https://i.niupic.com/images/2023/02/20/akDK.jpg',
    }
  },
  data() {
    return {
    };
  },
  computed: {

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
.logo {
    min-width: 90px;
    min-height: 80px;
    height: 100%;
  .image {
    width: 100%;
    height: 100%;
  }
}
</style>
  