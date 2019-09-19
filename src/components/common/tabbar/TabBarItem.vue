<template>
  <div class="tab-bar-item" @click='itemClick'>
    <slot v-if='!isActive' name="item-icon"></slot>
    <slot v-else name="item-icon-active"></slot>
    <div :class="{active: isActive}">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    path: String
  },
  data() {
    return {
      // isActive: false
    }
  },
  methods: {
    itemClick() {
      console.log(this.path)
      this.$router.replace(this.path)
    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    }
  }
}
</script>

<style scoped>
  .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }

  .tab-bar-item img {
      width: 24px;
      height: 24px;
      margin: 3px 0 3px;
      vertical-align: middle;
  }

  .active {
    color: #ff8198;
  }
</style>