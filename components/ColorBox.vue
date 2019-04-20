<template>
  <div
    @click="$emit('colorClicked', $event)"
    class="change-color"
  />
</template>

<script>
export default {
}
</script>

<style scoped>
.change-color {
  position: absolute;
  bottom: 0px;
  left:  0px;
  width: 40px;
  height: 40px;
  cursor: pointer;
}
</style>
