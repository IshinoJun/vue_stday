<template>
  <div
    class="add-button"
    @click="onClick"
  />
</template>

<script>
export default {
  methods: {
    onClick() {
      this.$emit('clicked')
    }
  }
}
</script>

<style>
.add-button {
  position: fixed;
  bottom: 20px;
  left: 20px;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: #fff;
  cursor: pointer;
}
</style>
