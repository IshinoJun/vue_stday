<template>
  <div
    class="drag-handler"
    @mousedown="$emit('dragStart', $event)"
  />
</template>

<script>
export default {
}
</script>

<style scoped>
.drag-handler {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  cursor: pointer;
}
</style>
