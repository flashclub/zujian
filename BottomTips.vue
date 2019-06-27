<template>
  <div
    v-bind:class="[isFocusFlag?'focus':'','fly-bottom-tips']"
    @click="closeWrap"
    v-if="showTips"
  >
    <div @click.stop="wrapContent">
      <img
        src="https://img.sfystatic.com/upload/tmp/images/activity/xyf-mobile/fly/left-icon.png"
        alt=""
        @click="closeWrap"
      >
      <p>
        {{titleText}}
      </p>
      <div>
        <slot></slot>
      </div>
      <button
        @click="clickFn"
        :class="buttomStyle?'active':''"
      >{{btnText}}</button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  props: {
    titleText: {
      //顶部文字内容
      default: '关联京东账户提示',
      type: String,
    },
    text: {
      //中间文字内容
      default: '示例内容',
      type: String,
    },
    btnText: {
      //底部按钮文案
      default: '注册',
      type: String,
    },
    buttomStyle: {
      //底部按钮样式
      default: false,
      type: Boolean,
    },
    showTips: {
      //是否显示对话框
      default: false,
      type: Boolean,
    },
    isFocusFlag:{
      default: false,
      type: Boolean
    }
  },
  mounted() {},
  methods: {
    closeWrap() {
      // this.showTips = false;
      console.log('关闭wrap');
      // this.showTips = false;
      this.$emit('close-wrap');
    },
    clickFn() {
      // this.showTips = false;

      this.$emit('click');
    },
    wrapContent(e) {},
  },
};
</script>
<style lang="less">
.fly-bottom-tips {
  position: absolute;
  top: 0rem;
  left: 0rem;
  right: 0rem;
  bottom: 0rem;
  background-color: rgba(0, 0, 0, 0.75);
  z-index: 100;
  display: flex;
  align-items: flex-end;
  flex-wrap: wrap;
  &.focus{
    align-items: center
  }
  .active {
    background-color: #1384ff;
  }
  > div {
    background-color: #fff;
    width: 100%;
    // position: absolute;
    // top: 0rem;
    // left: 0rem;
    // right: 0rem;
    // bottom: 0rem;

    > img {
      position: absolute;
      top: 0.373333rem;
      left: 0.533333rem;
      width: 0.213333rem;
    }
    > p {
      text-align: center;
      line-height: 1.066667rem;
      background-color: #f7f7f7;
      font-size: 0.426667rem;
      color: #353535;
      font-weight: 600;
    }
    > button {
      text-align: center;
      display: block;
      line-height: 1.013333rem;
      width: 2.933333rem;
      color: #fff;
      font-size: 0.373333rem;
      margin: auto;
      border-radius: 0.506667rem;
      margin-bottom: 0.64rem;
      // border-top: 0.026667rem solid #f0f0f0;
    }
  }
}
</style>
