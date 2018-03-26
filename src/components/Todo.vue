<template>
    <div>
        {{ msg }}
        <br/>
        <Task v-on:keyup.enter="add(taskName2)" v-model="currentTask" />
        <div class="ui list" v-for="task in tasklist" tag="ul">
            <div class="ui right labeled left icon input list" tag="li">
                <Task :taskName2="task.taskName2"  :fait2="task.fait2"/>
            </div>
        </div>
        {{ currentTask.taskName2}} {{ currentTask.fait2}}
    </div>
    
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
            msg: 'Welcome to To do list',
            tasklist : [{ taskName2 : 'blabla' , fait2 : true}, { taskName2 : 'blabla2' , fait2 : false} ],
            currentTask : {type : Task}
        }   
    },
    methods: {
        add(taskName2){
            this.currentTask.taskName2 = taskName2.srcElement.value;
            this.currentTask.fait2 = false;
            console.log('appel fct Add');
            console.log(this.currentTask);
            this.tasklist.push(this.currentTask);
        },
       
        remove(taskName2){
            //  supprimé l'item
            // l'index de l'élément: items.indexof(this.item)
            // suppréssion dasn le tableau this.items.slice(items.indexof(this.item),1)
            this.tasklist.splice(this.tasklist.indexOf(taskName2),1);
        }
    },
//    mounted: {
////        this.tasklist.push();
////        this.tasklist.push(null);
//    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
