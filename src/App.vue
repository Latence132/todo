<template>
<div class="ui center aligned container segment" style="{ background : #6f2929 }">
      <Todo/>
</div>
</template>

<script>
import Todo from './components/Todo'

export default {
  name: 'App',
  components: {
    Todo
  }
}
</script>

<style src="./todo.css">

</style>
