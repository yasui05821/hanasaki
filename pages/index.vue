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

      <Flower :imageDataList="imageDataList"></Flower>
    </div>
  </section>
</template>

<script>
import Flower from '~/components/Flower.vue'

import Image1 from '~/assets/images/01.jpg'
import Image2 from '~/assets/images/02.jpg'
import Image3 from '~/assets/images/03.jpg'
import Image4 from '~/assets/images/04.jpg'

export default {
  components: {
    Flower
  },
  data(){
    return {
      imageDataList : [ Image1, Image2, Image3, Image4 ]
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
</style>
