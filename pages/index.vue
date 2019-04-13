<template>
  <section
    class="container"
    @mouseup="dragEnd"
    @mousemove="dragging"
  >
    <div>
      <memo
        v-for="(memoInfo, i) in $store.state.memoInfoList"
        :key="i"
        :pos-x="memoInfo.posX"
        :pos-y="memoInfo.posY"
        :text="memoInfo.text"
        :index="i"
        @dragStart="dragStart(i, $event)"
        @dragEnd="dragEnd"
        @dragging="dragging"
      />
    </div>
    <add-btn @clicked="$store.commit('addMemo')" />
  </section>
</template>

<script>
import Memo from '~/components/Memo.vue'
import AddBtn from '~/components/AddBtn.vue'

export default {
  components: {
    Memo,
    AddBtn
  },
  data() {
    return {
      isDragging: false,
      draggingIndex: null,
      prevX: null,
      prevY: null
    }
  },
  methods: {
    dragStart(i, $event) {
      this.isDragging = true
      this.draggingIndex = i
      this.prevX = $event.pageX
      this.prevY = $event.pageY
    },
    dragEnd() {
      this.isDragging = false
      this.draggingIndex = null
    },
    dragging($event) {
      if (!this.isDragging) return

      this.$store.commit('dragMemo', {
        index: this.draggingIndex,
        deltaX: $event.pageX - this.prevX,
        deltaY: $event.pageY - this.prevY
      })

      this.prevX = $event.pageX
      this.prevY = $event.pageY
    }
  }
}
</script>

<style scoped>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background: center/cover url('~assets/background.jpeg');
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
