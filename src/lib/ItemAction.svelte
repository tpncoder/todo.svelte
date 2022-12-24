<script>
import Task from './Item.svelte'
import { getNotificationsContext } from 'svelte-notifications';

const { addNotification } = getNotificationsContext();

let name = ''
let tasks = []

function addTask(name){
	if(name.length > 0 && name.trim().length > 0){
		tasks = [...tasks, {task: name}]
		addNotification({
			text: 'Task Added!',
			position: 'top-right',
			type: 'success'
		})
	}
	else{
		addNotification({
			text: 'Empty Task Name',
			position: 'top-right',
			type: 'warning'
		})
	}

	console.log(`Task Added: ${name}`)
}

function removeTask(index){
	tasks = tasks.filter(item => item !== tasks[index])	
	addNotification({
		text: 'Task Removed!',
		position: 'top-right',
		type: 'error'
	})
	
	console.log(`Task Removed: ${name}`)
}
</script>

<input bind:value={name} placeholder="Enter task name">
<button on:click={() => addTask(name)} class='add'>ADD TASK</button>

<h1 style={'text-decoration: underline; margin-left: 1em'}>todo</h1>

{#each tasks as task, index}
	{#if task.task.length > 0}	
		<div class='card'>
			<Task content={task.task}/>
			<button on:click={()  => removeTask(index)} class='remove'><span class="material-symbols-outlined">done</span></button>
		</div>
	{/if}
{/each}

<style>
input{
	width: 30%;
	padding: 1em;
	font-size: 1em;
	border: 1px solid gray;
	outline: none;
	margin-left: 1em;
}

.add{
	font-size: 1em;
	padding: 1em;
	margin-left: -0.3%;
	border: 1px solid salmon;
	background-color: salmon;
	color: white;
	cursor: pointer;
}

.remove{
	border: none;
	background-color: transparent;
	cursor:  pointer;
}

.card{
	display: block;
	position: relative;
	margin-left: 1em;
	padding: 1em;
	border: 1px solid salmon;
	margin-bottom: 1em;
}
</style>
