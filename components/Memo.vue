<template>
  <div
    :style="{
      top: `${posY}px`,
      left: `${posX}px`
    }"
    class="memo"
  >
    <drag-handler
      @dragStart="$emit('dragStart', $event)"
    />
    <remove-btn @remove="$store.commit('removeMemo', index)" />
    <text-box
      :text="text"
      @inputed="onInputed"
    />
  </div>
</template>

<script>
import DragHandler from '~/components/DragHandler.vue'
import TextBox from '~/components/TextBox.vue'
import RemoveBtn from '~/components/RemoveBtn.vue'

export default {
  components: {
    DragHandler,
    TextBox,
    RemoveBtn
  },
  props: {
    posX: {
      type: Number,
      required: true
    },
    posY: {
      type: Number,
      required: true
    },
    text: {
      type: String,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    onInputed(text) {
      this.$store.commit('setText', {
        text,
        index: this.index
      })
    }
  }
}
</script>

<style scoped>
.memo {
  position: fixed;
  width: 200px;
  height: 300px;
  background: #ff0;
}
</style>
