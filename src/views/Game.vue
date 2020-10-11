<template>
  <div id='Game'>
    <p>じゃんけん！</p>
    <div v-if="pon">
    <img height="100px" v-if="this.bot === 0" src="@/assets/gu.png">
    <img height="100px" v-if="this.bot === 1" src="@/assets/choki.png">
    <img height="100px" v-if="this.bot === 2" src="@/assets/par.png">
    </div>
    <div v-show="showp" v-if="you">
    <img height="100px" v-if="this.player === 0" src="@/assets/gu.png">
    <img height="100px" v-if="this.player === 1" src="@/assets/choki.png">
    <img height="100px" v-if="this.player === 2" src="@/assets/par.png">
    </div>
    <div v-else>
    <img width="150px" class="animation" src="@/assets/facep.png">
    </div>
    <br>
    <button v-show="shows" v-for="item in items" :key="item.key" @click="select(item.key)">
      <img :src="item.src" height="100px"/>
    </button>
    <p>この勝負…<span v-html="resultText"></span></p>
    <button v-show="show" @click="retry"><h1>もう一度！</h1></button>
  </div>
</template>
<script>
export default {
  name: 'Game',
  data () {
    return {
      items: [
        { src: require('@/assets/gu.png'), key: 0 },
        { src: require('@/assets/choki.png'), key: 1 },
        { src: require('@/assets/par.png'), key: 2 }
      ],
      resultText: '',
      player: '',
      you: false,
      pon: false,
      show: false,
      showp: false,
      shows: true
    }
  },
  methods: {
    select (key) {
      this.you = true
      this.pon = true
      this.player = key
      this.result()
      this.show = true
      this.showp = true
      this.shows = false
    },
    retry () {
      this.you = false
      this.pon = false
      this.resultText = ''
      this.player = ''
      this.show = false
      this.showp = false
      this.shows = true
    },
    result () {
      this.bot = Math.floor(Math.random() * 3)
      switch (((this.player - this.bot + 3) % 3)) {
        case 0:
          this.resultText = '引き分けっ'
          break
        case 1:
          this.resultText = '<span style="color: blue">あなたの負け…</span>'
          break
        case 2:
          this.resultText = '<span style="color: red">あなたの勝ち！</span>'
          break
      }
    }
  }
}
</script>

<style>
button {
  -webkit-appearance: none;
  border-radius: 0;
}
</style>
