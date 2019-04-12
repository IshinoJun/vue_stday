<template>
  <div
    class="drag-handler"
    @mousedown="touchstart"
    @mousemove="touchmove"
    @mouseup="touchend"
    @mouseleave="touchend"
  />
</template>

<script>
export default {
  prev_posx: 0,
  prev_posy: 0,
  is_mousedown: false,
  methods: {
    touchstart(e) {
      this.is_mousedown = true
      this.prev_posx = e.offsetX
      this.prev_posy = e.offsetY
    },
    touchmove(e) {
      if (this.is_mousedown) {
        this.movedx = e.offsetX - this.prev_posx
        this.movedy = e.offsetY - this.prev_posy
        this.$emit('movedx', this.movedx)
        this.$emit('movedy', this.movedy)
      }
    },
    touchend(e) {
      this.is_mousedown = false
    }
  }
}

</script>
<style>
.drag-handler {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  cursor: pointer;
}
</style>
