<template>
  <div
    :style="{
      top: `${posY}px`,
      left: `${posX}px`,
      background: bgColor
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
    <div class="color-pallet">
      <color-box
        v-for="color in colorList"
        :key="color"
        :color="color"
        :index="index"
      />
    </div>
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
    bgColor: {
      type: String,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  computed: {
    colorList: () => ['#f00', '#0f0', '#00f', '#ff0']
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
}

.color-pallet {
  position: absolute;
  bottom: 0;
}
</style>
