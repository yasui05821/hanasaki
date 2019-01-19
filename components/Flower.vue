<template>
  <div class="flower" ref="flower">
    <img :src="activeImageUrl" alt="" class="flower-view" @load="loaded">
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
export default {
  props : {
    imageDataList : Array
  },
  components: {
    Logo
  },
  data(){
    return {
      scrollY : 0, //現在のスクロール位置
      offsetTop: null, // お花要素のページ内の縦位置
      offsetHeight: null, // お花要素の高さ
      innerHeight: null, // Window の高さ
      grid: 0 // 咲くために必要な変化する高さの段階割合
    }
  },
  mounted() {
    // スクロールに反応して Vue.js が動くようにする
    window.addEventListener('scroll', this.handleScroll);
    window.addEventListener('resize', this.handleScroll);
    // mounted のタイミングではまだ DOM が存在しない
  },
  computed:{
    windowBottom(){
      return this.scrollY + this.innerHeight
    },
    gridHeight(){
      // 半分の位置から n段階で切り替えたいから
      console.log(this.offsetHeight , (this.imageDataList.length))
      return this.offsetHeight / (this.imageDataList.length)
    },
    activeImageUrl(){
      let n = Math.floor(this.position() / this.gridHeight)
      return this.imageDataList[Math.min(this.imageDataList.length-1,Math.max(0,n))] //List外にださない
    }
  },
  methods:{
    loaded(){
      this.offsetTop = this.$refs.flower.offsetTop
      this.offsetHeight = this.$refs.flower.offsetHeight
    },
    handleScroll() {
      // 実際のスクロール位置を Vue.js の変数に格納
      this.innerHeight = window.innerHeight
      this.scrollY = window.scrollY
    },
    position(){
      // 変化に必要な変数を常に計算させる
      // 半分の位置から切り替える
      return this.windowBottom - this.offsetTop - (this.offsetHeight / 2) + this.gridHeight || -1
    },
  }
}
</script>

<style lang="scss" scoped>
.flower {
  img {
    width: 100%;
    display: block;
  }
}
</style>

