<template>
    <section class="todoapp">
       <header class="header"><h1>{{msg}}</h1></header>
        
        <br/>
        <ul>
            <div class="ui right labeled left icon input">
                <input type="text" v-on:keyup.enter="add(currentTask)" v-model="currentTask" value="currentTask">
                 <a class="ui tag label"  @click="$parent.done(taskName2)" name="taskNameDone">
                  <i class="check icon"></i>
                </a>
                <a class="ui tag label" @click="$parent.remove(taskName2)" name="taskNameTrash">
                   <i class="trash icon"></i>
                </a>
            </div>
        
            <div class="ui list" v-for="task in filteredTasktlist">
               <li :class="{completed : task.fait2}">
                    <div class="ui right labeled left icon input list"  >
                        <Task :taskName2="task.taskName2"  :fait2="task.fait2"  tag="li"/>
                    </div>
               </li>
            </div>
        </ul>
        <footer>
            <span class="todo-count">tâches à faire :<strong>{{remaining}}</strong> </span>
            <br/>
            <ul class="filters">
                <li><a href="#" :class="{selected: filter === 'all'}" @click.prevent="filter = 'all'">Toute</a></li>
                <li><a href="#" :class="{selected: filter === 'todo'}" @click.prevent="filter = 'todo'">A faire</a></li>
                <li><a href="#" :class="{selected: filter === 'done'}" @click.prevent="filter = 'done'">Fait</a></li>
               
            </ul>
        </footer>
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
//            this.currentTask.taskName2 = taskName2.srcElement.value;
//            this.currentTask.fait2 = false;
            console.log('appel fct Add');
            console.log(this.currentTask);
            this.tasklist.push({taskName2:this.currentTask, fait2:false});
        },
        remove(taskName2){
            //  supprimé l'item
            // l'index de l'élément: items.indexof(this.item)
            // suppréssion dasn le tableau this.items.slice(items.indexof(this.item),1)
            console.log(this.tasklist.filter(task => task.taskName2 == taskName2));
            this.tasklist.splice(this.tasklist.filter(task => task.taskName2 == taskName2),1);
        },
        done(taskName2){
            console.log('fonction done parent');
//            console.log(taskName2);
            console.log(this.task);
            console.log(this.tasklist.filter(task => task.taskName2 == taskName2)[0].fait2);
            this.tasklist.filter(task => task.taskName2 == taskName2)[0].fait2 = !this.tasklist.filter(task => task.taskName2 == taskName2)[0].fait2
            

//            console.log(this.tasklist.indexOf(taskName2));
//            task.fait2 = !task.fait2

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
            
        }
    }
//    mounted: {
////        this.tasklist.push();
////        this.tasklist.push(null);
//    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >

</style>
