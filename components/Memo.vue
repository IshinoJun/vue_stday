<template>
  <div
    :style="{
      top: `${posY}px`,
      left: `${posX}px`
    }"
    class="memo">
  </div>
</template>

<script>
export default {
  props: {
    posX: {
      type: Number,
      required: true
    },
    posY: {
      type: Number,
      required: true
    }
  }
}
</script>

<style>
.memo {
  position: fixed;
  width: 200px;
  height: 300px;
  background: #ff0;
}
</style>
