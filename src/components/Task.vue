<template>
    <div>
        <div class="ui right labeled left icon input">
            <input type="text" v-on:keyup.enter="$parent.add" v-model="taskName2" :name="taskName2" :style="style">
             <a class="ui tag label"  @click="$parent.done(taskName2)" name="taskNameDone">
			  <i class="check icon"></i>
			</a>
       		<a class="ui tag label" @click="$parent.remove(taskName2)" name="taskNameTrash">
               <i class="trash icon"></i>
            </a>
        </div>
    </div>
</template>
<script>
export default {
  name: 'Task',
  props : {
      taskName2: {type : String, default : 'Nouvelle chose à faire'},
      fait2: {type : Boolean, default : false }
  },
  methods:{
//	done () {
//      //  barré la chose faire
//	  console.log('Appel fct done()');
//	  this.fait2 = !this.fait2 
//    },
//	remove (){
//		console.log('Appel fct destroy()');
//		this.$destroy()
//	},
    rename (taskName) {
      console.log('fonction rename');
      this.taskName = this.taskName2
      console.log(this.taskName2)
    }
  },
  computed: {
	style () {
	  if (this.fait2) {
        return {'text-decoration': 'line-through'}
      }
	else {
		return {'text-decoration': 'underline'}
	  }
	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
