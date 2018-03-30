<template>
<div>
<!--
    <div class="ui center aligned container segment">
        <Todo/>
    </div>
-->
    <div>
        <caroussel>
           <caroussel-slide v-for="n in slides" :index="n-1">
               <div style="position : absolute; text-align: center; left:0; right:0; top:50% ;color: #FFF;">Slide {{ n }}</div>
               <img :src="'http://lorempicsum.com/nemo/630/300/' + n" alt="'nemo'+caroussel.index" width="100%">
           </caroussel-slide>
    
        </caroussel>
        <button @click="addSlide">Ajouter un slide</button>
        <button @click="removeSlide">Supprimer un slide</button>
    </div>
</div>

</template>

<script>
//    import Todo from './components/Todo'
    import Caroussel from './components/Caroussel/Caroussel'
    import CarousselSlide from './components/Caroussel/CarousselSlide'

    export default {
        name: 'App',
        components: {
//            Todo,
            Caroussel,
            CarousselSlide
        },
        data (){
            return {
                slides: 5
            }
        },
        methods:{
            addSlide () {
                this.slides++;
            },
            removeSlide () {
                this.slides--;
            }
        }
    }
</script>

<style src="./todo.css">


</style>
