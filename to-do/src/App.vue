<template>
  <div id="app">
    <h1 style="margin-bottom: 30px">My Tasks</h1>
	<task-progress :progress="progress"/>
	<new-task @taskAdded="addTask"/>
    <tasks-grid
	:tasks="tasks"
	@deletedTask="deleteTask"
	@taskStateChanged="toogleTaskState"
	/>
  </div>
</template>

<script>

import TasksGrid from './components/TasksGrid.vue'
import NewTask from './components/NewTask.vue'
import TaskProgress from './components/TaskProgress.vue'

export default {
  name: 'App',
  components:{TasksGrid, NewTask, TaskProgress},

  data(){
    return{
      tasks: []
    }
  },
  computed:{
	progress(){
		const total = this.tasks.length
		const done = this.tasks.filter(t => !t.pending).length
			
		return Math.round(done / total * 100) || 0
	}
},
  methods:{
	addTask(task){
		const sameName = item => item.name === task.name

		const reallyNew = this.tasks.filter(sameName).length == 0

		if(reallyNew){
			this.tasks.push({
				name: task.name,
				pending: task.pending || true
			})
		}
	},
	deleteTask(index){
		this.tasks.splice(index, 1)
	},
	toogleTaskState(index){
		this.tasks[index].pending = !this.tasks[index].pending
	}
  }
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(15, 11, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
