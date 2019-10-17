<template>
  <div id="app">
    <TaskBoard/>
  </div>
</template>

<script>
import TaskBoard from './components/TaskBoard'

export default {
  name: 'app',
  components: {
    TaskBoard
  }
}
</script>

<style>
body {
  background: linear-gradient(45deg, #EECFBA, #C5DDE8);
	display: flex;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  width: 100%;
}
</style>
