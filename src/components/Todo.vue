<template>
    <section class="todoapp">
      
       <header class="header"><h1>{{msg}}</h1></header>
        

        <div class="main">
        <ul class="todo">
            <div class="ui    input">
                <input type="text" v-on:keyup.enter="add(currentTask)" v-model="currentTask" value="currentTask">
   
            </div>
        
            <div class="ui list" v-for="task in filteredTasktlist">
               <li :class="{completed : task.fait2 }">
                    <div class="ui right labeled left icon input list"  >
                        <Task :taskName2="task.taskName2"  :fait2="task.fait2"  @blur="doneEdit(task)" tag="li"/>
                    </div>
               </li>
            </div>
        </ul>
        <footer v-show="tasklist.length >0">
            <span class="todo-count">tâches à faire :<strong>{{remaining}}</strong> </span><br/>
            <input type="checkbox" class="toggle-all" v-model="allDone"><br/>
            <ul class="filters">
                <li><a href="#" :class="{selected: filter === 'all'}" @click.prevent="filter = 'all'">Toute</a></li>
                <li><a href="#" :class="{selected: filter === 'todo'}" @click.prevent="filter = 'todo'">A faire</a></li>
                <li><a href="#" :class="{selected: filter === 'done'}" @click.prevent="filter = 'done'">Fait</a></li>
            </ul>
            <button class="clear-completed" @click.prevent="removeDone()" v-show="remaining < tasklist.length">Clear done</button>
        </footer>
        </div>
    </section>
    
</template>
<script>
import Task from './Task'
export default {
name: 'To-do-list',
    components:{
        Task
    },
    data () {
        return {
            msg: 'To do list',
            tasklist : [{ taskName2 : 'blabla' , fait2 : true}, { taskName2 : 'blabla2' , fait2 : false} ],
            currentTask : 'nouvelle tache',
            filter: 'all'
        }   
    },
    methods: {
        add(){
//            méthode plus compliqué, a ne pas utilisé
//            this.currentTask.taskName2 = taskName2.srcElement.value;
//            this.currentTask.fait2 = false;
//            console.log('appel fct Add');
//            console.log(this.currentTask);
            
            this.tasklist.push({taskName2:this.currentTask, fait2:false});
        },
        remove(taskName2){
            //  supprimer l'item, méthode complexe a ne pas utilisé
            // l'index de l'élément: items.indexof(this.item)
            // suppréssion dasn le tableau this.items.slice(items.indexof(this.item),1)
            // console.log(this.tasklist.filter(task => task.taskName2 == taskName2));
            // this.tasklist.splice(this.tasklist.filter(task => task.taskName2 == taskName2),1);
            
            this.tasklist = this.tasklist.filter( task => task.taskName2 !== taskName2);
        },
        done(taskName2){
            //cette tache peut être plus simple a réaliser en changeant l'icone par une checkbox
//            console.log('fonction done parent');
//            console.log(taskName2);
            console.log(this.tasklist.filter(task => task.taskName2 == taskName2)[0].taskName2);
            console.log(this.tasklist.filter(task => task.taskName2 == taskName2)[0].fait2);
            this.tasklist.filter(task => task.taskName2 == taskName2)[0].fait2 = !this.tasklist.filter(task => task.taskName2 == taskName2)[0].fait2
//            console.log(this.tasklist.indexOf(taskName2));
//            task.fait2 = !task.fait2

        },
        removeDone(){
            this.tasklist = this.tasklist.filter(task => task.fait2 === false);
        },
        doneEdit(){
            console.log("edittask");
            this.tasklist.filter(task => task.taskName2 === task.taskName2)[0].taskname2 = this.task.taskName2;
        }
    },
    computed:{
        remaining(){
            console.log('changement remaining')
            return this.tasklist.filter(task => !task.fait2).length
        },
        filteredTasktlist(){
            if(this.filter ==='todo'){
                return this.tasklist.filter( task => !task.fait2)
            } 
            else if(this.filter ==='done'){
                return this.tasklist.filter( task => task.fait2)
            } 
            else {
                return this.tasklist
            }
        },
        allDone:{
            set(value){
                    this.tasklist.forEach(task => {task.fait2 = value})
            },
            get(){
            return this.remaining === 0;
            }
        },
        Task:{
            get(){
                return this.task;
            }
        }
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >

</style>
