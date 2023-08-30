<template>
    <el-form v-if="currentComponent" :model="form" label-position="top" @click.native.stop>
      <el-tabs v-model="tab" type="border-card">
        <el-tab-pane label="内容" name="content">
          <el-form-item label="logo路径">
            <var-input  v-model="currentComponent.props.src" type="textarea" :rows="5" resize="none" ></var-input>
          </el-form-item>
          <el-form-item>
            <el-upload
              action="https://jsonplaceholder.typicode.com/posts/"
              :show-file-list="false"
              :on-success="handleAvatarSuccess"
              >
              <el-button type="primary">上传图片</el-button>
            </el-upload>
          </el-form-item>
          <el-form-item>
              <el-button type="danger" @click="deletes">删除标签</el-button>
          </el-form-item>
        </el-tab-pane>
      </el-tabs>
    </el-form>
  </template>

  <script>
  import { mapGetters } from 'vuex';
  export default {
    data() {
      return {
        tab: 'content',
        form: {
        },
        debounceUpdate: Function,
      };
    },
    computed: {
      ...mapGetters(['activeComponent', 'storeList']),
      currentComponent() {
        return this.storeList.find((item) => item.id === this.activeComponent.id);
      },
    },
    methods: {
      handleAvatarSuccess(res, file) {
       console.log(res, file);
      },
      init() {
        // doing
      },
      deletes(){
          this.$store.dispatch('components/deleteComponent',this.currentComponent);
        }
    },
  };
  </script>
  
  <style lang="scss">
  @import "./src/style/variable";
  .barcode-menu-warp {
    height: calc(100% - 53px);
    display: flex;
    flex-direction: column;
    .bottom-handle {
      display: flex;
      align-items: center;
      padding: 14px;
      .el-button {
        width: 50%;
      }
    }
  }
  </style>
  