<template>
  <section class="container">
    <div>
      <memo
        v-for="(memoInfo, i) in memoInfoList"
        :key="i"
        :posX="memoInfo.posX"
        :posY="memoInfo.posY"
        :text="memoInfo.text"
        @inputed="setText($event, i)"
      />
    </div>
    <add-btn @clicked="addMemo" />
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
      memoInfoList: [
        {
          posX: 20,
          posY: 20,
          text: 'tafagawhagta'
        }
      ]
    }
  },
  methods: {
    addMemo() {
      const lastMemo = this.memoInfoList[this.memoInfoList.length - 1]

      this.memoInfoList = [
        ...this.memoInfoList,
        {
          posX: lastMemo.posX + 220,
          posY: lastMemo.posY + 20,
          text: ''
        }
      ]
    },
    setText(text, i) {
      this.memoInfoList = this.memoInfoList.map((memoInfo, index) => {
        if (i === index) {
          return {
            ...memoInfo,
            text
          }
        } else {
          return memoInfo
        }
      })
    }
  }
}
</script>

<style>
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
