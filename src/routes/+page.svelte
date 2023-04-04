<script>
    let title = "Kayla's ToDo App";
    let tasks = [
        { id: 1, name: 'My journey with Svelte', status: true },
        { id: 2, name: 'Blogging with Svelte', status: false },
        { id: 3, name: 'Why Svelte is so fun', status: true }
    ];


    let newTask = {
        id: 0,
        name: '',
        status: false
    };

    let addTask = () => {
        tasks = tasks.concat({
            id: tasks.length + 1,
            name: newTask.name,
            status: newTask.status
        })
    }

    let deleteTask = (id) => {
        tasks = tasks.filter(task => task.id !== id)
        tasks.splice(tasks.length - 0)
        tasks = tasks
        console.log(tasks)
    }

    


</script>
<div class="main">
<h1>{title}</h1>
<div>
    <input type="text" bind:value={newTask.name} placeholder="Enter new task...">
    <button on:click={addTask}>Add Task</button>
    
    <table>
        <thead>
            <tr>
                <th>Task</th>
                <th>Status</th>
                <th>Delete</th>
            </tr>
        </thead>
        <tbody>
            {#each tasks as task}
            <tr>
                <td>
                    <input class:checked={task.status} class="taskName" type="text" bind:value={task.name} placeholder="Enter task name...">
                </td>
                <td>
                    <input type="checkbox" bind:checked={task.status}>
                </td>
                <td>
                    <button on:click={() => deleteTask(task.id)}>-</button>
                </td>
            </tr>
            {/each}
        </tbody>
    </table>
</div>
</div>

<style> 
.main{
    padding: 2%;
}
table{
    padding-top: 20px;
}
tr, td{
    padding: 20px
}
.taskName{
    border: none;
    border-bottom: 1px solid black;
}
	.checked {
        text-decoration: line-through;
    }
</style> 