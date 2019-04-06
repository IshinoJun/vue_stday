<template>
  <textarea
    class="text-box"
    :value="text"
    @input="onInput"
  />
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    }
  },
  methods: {
    onInput(e) {
      this.$emit('inputed', e.target.value)
    }
  }
}
</script>

<style>
.text-box {
  position: absolute;
  display: block;
  bottom: 0;
  top: 60px;
  left: 0;
  width: 100%;
  background: transparent;
}
</style>
