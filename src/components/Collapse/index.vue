<template>
  <div class="collapse-wrap">
    <div class="header">
      <div class="title">
        <slot name="ico"></slot>
        <b>{{ title }}</b>
      </div>
      <div
        class="ico-wrap"
        @click="isOpen = isOpen ? false : true"
      >
        <i
          :class="{
            ico: true,
            'el-icon-arrow-up': true,
            down: !isOpen ? true : false,
          }"
        ></i>
      </div>
    </div>
    <div class="content">
      <div v-show="isOpen">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    title: {
      type: String,
      require: true,
      default: '',
    },
    open: {
      type: Boolean,
      require: true,
    },
  },
  data() {
    return {
      isOpen: false,
    };
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {
    this.isOpen = Boolean(this.open);
  },
  methods: {
    handleClick() {},
  },
};
</script>

<style lang="scss" scoped>
.collapse-wrap {
  // overflow: hidden;
  margin-top: 20px;
  padding: 10px;
  border: 1px solid $theme-color4;
  border-radius: 6px;
  background: $theme-color6;

  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    .title {
      margin: 8px 0;
    }
    .ico-wrap {
      width: 20px;
      height: 20px;
      cursor: pointer;
      transform: translateY(2px);
      .ico {
        transition: all 0.3s;
        transform: rotate(0deg);
        &.down {
          transform: rotate(180deg);
        }
      }
    }
  }
  .content {
    height: 100%;
    transition: height 0.5s;
    .item {
      margin-bottom: 4px;
    }
  }
}
</style>
