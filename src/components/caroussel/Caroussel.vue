<template>
    <div class="carousel">
      <slot></slot>
      <button class="carousel__nav" @click.prevent="prev"></button>
      <button class="carousel__nav carousel__next" @click.prevent="next"></button>
      <div class="carousel__pagination">
          <button v-for="n in slidesCount" @click="goto(n-1)" :class="{active: n-1 == index}"></button>
      </div>
    </div>
</template>


<script>
    export default {
        name:"Caroussel",
        data () {
            return {
                index: 0,
                slides: [],
                direction :'right'
            }
        },
        watch:{
            slides (slides) {
                if( this.index >= this.slidesCount){
                    this.index = this.slidesCount-1;
                }
            }
        },
        computed:{
          slidesCount() { return this.slides.length}  
        },
        methods: {
            next(){
                this.index++;
                this.direction ='right';
                if( this.index >= this.slidesCount){
                    this.index = 0;
                }
            },
            prev() {
                this.index--;
                this.direction ='left';
                 if( this.index < 0){
                    this.index = this.slidesCount - 1 ;
                }
            },
            goto(index) {
                this.direction = index >this.index ? 'right' : 'left';
                this.index = index;
            }
        },
        mounted () {
            this.slides = this.$children;
            // pose des problèmes lors d'ajout de slides dynamique
//            this.slides.forEach((slide,i) => {
//                slide.index = i;
//            })
        }
     
    }

</script>


<style>
    .carousel{
        position: relative;
        width: auto;
        
    }
    
    .carousel__nav{
        position:  absolute;
        top: 50%;
        margin-top: -11px;
        left: 10px;
        background: url(prev_arrow2.png);
        width: 15px;
        height: 22px;

    }
    
     .carousel__nav.carousel__next{
        left: auto;
        right: 10px;
        background: url(next_arrow2.png);

    }
    
    .carousel__pagination {
        position: absolute;
        bottom: 2px;
        left: 0;
        right: 0;
        text-align: center; 
    }
    
    .carousel__pagination button {
        display: inline-block;
        width: 10px;
        height: 10px;
        background-color: #000;
        opacity: 0.8;
        border-radius: 10px;
        margin: 0 2px;
    }
     .carousel__pagination button.active {
         background-color: #FFF;
    }

</style>