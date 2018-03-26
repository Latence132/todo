<template>
    <div>
        <div class="ui input" >
            <input type="text" v-on:keyup.enter="rename" v-model="taskName" name="taskName" :style="style">
             <a class="ui tag label"  @click="done()" name="taskNameDone">
			  <i class="check icon"></i>
			</a>
       		<a class="ui tag label" @click="remove()" name="taskNameTrash">
               <i class="trash icon"></i>
            </a>
        </div>
    </div>
</template>
<script>
export default {
  name: 'Task',
  data () {
    return {
      taskName: 'Nouvelle chose à faire',
      fait: false
    }
  },
  methods:{
	done () {
      //  barré la chose faire
	  console.log('Appel fct done()');
	  this.fait = !this.fait 
    },
	remove (){
		console.log('Appel fct destroy()');
		this.$destroy()
	},
    rename (taskName) {
      this.taskName = this.taskName
      console.log(this.taskName)
    },
  },
  computed: {
	style () {
	  if (this.fait) {
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
