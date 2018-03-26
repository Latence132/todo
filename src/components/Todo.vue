<template>
    <div>
        {{ msg }}
        <br/>
        <Task/>
<!--
        <div class="ui input" >
            <input type="text" v-on:keyup.enter="add" v-model="nouvelItem" name="nouvelItem" >
        </div>
-->
        <div class="ui list" v-for="item in items" :key="item">
            <div class="ui right labeled left icon input list" >
                <i class="tags icon"></i>
                <input type="text" placeholder="Chose à faire"  :value="item" :name="item" :class="done">
                <a class="ui tag label"  @click="done(item)" :name="item">
                     <i class="check icon"></i>
                </a>
                <a class="ui tag label" @click="remove(item)" :name="item">
                   <i class="trash icon"></i>
                </a>
            </div>
        </div>
    </div>
</template>
<script>
import Task from './Task'
export default {
name: 'To-do-list',
    data () {
        return {
			Task : { taskName : 'Nouvelle chose à faire', fait: false},
            nouvelItem: 'Nouvelle chose à faire',
            msg: 'Welcome to To do list',
            items: ['JS', 'Vuejs', 'NodeJS']
        }   
    },
    methods: {
        add(){
                console.log('appel fct Add');
                this.items.push(this.nouvelItem)
        },
       
        remove(item){
            //  supprimé l'item
            // l'index de l'élément: items.indexof(this.item)
            // suppréssion dasn le tableau this.items.slice(items.indexof(this.item),1)
            this.items.splice(this.items.indexOf(item),1);
        }
    },
    computed:{
         done(item){
            //  barré la chose faire
            console.log('appel fct Done');
            return {  'text-decoration': 'line-through'}
        },
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .done{
        text-decoration: line-through;
    }
</style>
