<template>
  <div
    class="remove-button"
    @click="$emit('remove')"
  >X</div>
</template>

<script>
export default {

}
</script>

<style scoped>
.remove-button {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 20px;
  cursor: pointer;
}
</style>
