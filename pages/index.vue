<template>
  <section class="container">
    <div class="container">
      <h1 class="title">
        hanasaki
      </h1>
      <div class="lorem">
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
      </div>
      <div class="lorem">
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid autem culpa eum expedita inventore iusto maxime mollitia, nisi odit quo tempore, tenetur totam? Debitis ducimus eligendi ex fuga nisi voluptatem.</p>
      </div>

      <div class="flower" ref="flower">
        <img src="~/assets/images/01.jpg" alt="">
        <img :src="activeImageUrl" alt="" class="flower-view">
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
export default {
  components: {
    Logo
  },
  data(){
    return {
      imageList:['01.jpg','02.jpg','03.jpg','04.jpg'],
      imageDataList:[],
      scrollY : 0, //現在のスクロール位置
      offsetTop: null, // お花要素のページ内の縦位置
      offsetHeight: null, // お花要素の高さ
      innerHeight: null, // Window の高さ
      grid: 0 // 咲くために必要な変化する高さの段階割合
    }
  },
  created(){
    Promise.all(this.imageList
    .map(name=>import(`~/assets/images/${name}`)))
    .then(list=>{
      this.imageDataList=list.map(x=>x.default)
    })
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
      return this.flower().offsetHeight / (this.imageDataList.length)
    },
    activeImageUrl(){
      let n = Math.floor(this.position() / this.gridHeight)
      return this.imageDataList[Math.min(this.imageDataList.length-1,Math.max(0,n))] //List外にださない
    }
  },
  methods:{
    flower(){
      return this.$refs.flower || {}
    },
    handleScroll() {
      // 実際のスクロール位置を Vue.js の変数に格納
      this.innerHeight = window.innerHeight
      this.scrollY = window.scrollY
    },
    position(){
      // 変化に必要な変数を常に計算させる
      // 半分の位置から切り替える
      return this.windowBottom - this.flower().offsetTop - (this.flower().offsetHeight / 2) + this.gridHeight || -1
    },
  }
}
</script>

<style lang="scss" scoped>
.container {
  margin:  0 auto;
  padding: 50px 10px;
  max-width: 375px;
}

.flower {
  position: relative;
  img {
    width: 100%;
    display: block;
    &.flower-view {
      position: absolute;
      top:0;
    }
  }
}
</style>
