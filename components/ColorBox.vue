<template>
  <div
    class="color-box"
    :style="{ background: color }"
    @click="changeColor"
  />
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    changeColor() {
      this.$store.commit('setColor', {
        color: this.color,
        index: this.index
      })
    }
  }
}
</script>

<style scoped>
.color-box {
  width: 50px;
  height: 50px;
  float: left;
}
</style>
