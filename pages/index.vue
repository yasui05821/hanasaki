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

      <div class="flower">
        <img :class="isActive" src="~/assets/images/01.jpg" alt="">
        <img :class="isActive2" src="~/assets/images/02.jpg" alt="">
        <img :class="isActive3" src="~/assets/images/03.jpg" alt="">
        <img :class="isActive4" src="~/assets/images/04.jpg" alt="">
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
    // mounted のタイミングではまだ DOM が存在しない
    this.$nextTick(()=>{
      // document.querySelector で お花の要素をとってくる
      const flower = document.querySelector(".flower")
      this.offsetTop = flower.offsetTop // 実際のお花要素のページ内の縦位置
      this.offsetHeight = flower.offsetHeight // 実際のお花要素のページ内の高さ
      this.grid = this.offsetHeight / 6 // 半分の位置から 3段階で切り替えたいから ÷6
      this.innerHeight = window.innerHeight // 実際の window の高さ
    })
  },
  computed:{
    position(){
      // 変化に必要な変数を常に計算させる
      if(this.offsetTop === null){
        return -1
      }
      return this.scrollY + this.innerHeight - this.offsetTop - (this.offsetHeight / 2)
    },
    isActive(){
      return {
        active: this.position < 0
      }
    },
    isActive2(){
      return {
        active: 0 <= this.position && this.position < this.grid
      }
    },
    isActive3(){
      return {
        active: this.grid <= this.position && this.position < (this.grid * 2)
      }
    },
    isActive4(){
      return {
        active: (this.grid * 2 )<= this.position
      }
    }
  },
  methods:{
    handleScroll() {
      // 実際のスクロール位置を Vue.js の変数に格納
      this.scrollY = window.scrollY
    }
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
  img{
    display: none;
  }
  img.active{
    width: 100%;
    display: block;

  }
}
</style>
