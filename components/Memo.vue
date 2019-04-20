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
    <color-box
      v-for="i in backgroundColorList.length"
      @colorClicked="colorClicked(i, $event)"
        :key="i"
        :index="i"
        :style="{
          left: `${40*i-40}px`,
          background: `${backgroundColorList[i-1]}`
        }"
     />
  </div>
</template>

<script>
import DragHandler from '~/components/DragHandler.vue'
import TextBox from '~/components/TextBox.vue'
import RemoveBtn from '~/components/RemoveBtn.vue'
import ColorBox from '~/components/ColorBox.vue'
export default {
  components: {
    DragHandler,
    TextBox,
    RemoveBtn,
    ColorBox
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
  data: function () {
    return {
      backgroundColorList: ['red', 'yellow', 'blue', 'green', 'pink']
    }
  },
  methods: {
    onInputed(text) {
      this.$store.commit('setText', {
        text,
        index: this.index
      })
    },
    colorClicked(i, $event) {
      this.$store.commit('colorChange', i)
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
