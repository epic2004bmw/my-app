<script>
	let projects = [
		{ projectID: 1, name: 'Archero' },
		{ projectID: 2, name: 'TodoA' }
	];

	let todos = [
		{
			todoID: 1,
			title: '30 situps',
			projectID: 1,
			completed: false
		},
		{
			todoID: 2,
			title: '20 pushups',
			projectID: 1,
			completed: false
		},
		{
			todoID: 3,
			title: '5 pull ups',
			projectID: 1,
			completed: false
		},
		{
			todoID: 4,
			title: 'Dailies',
			projectID: 2,
			completed: false
		},
		{
			todoID: 5,
			title: '5 Bosses',
			projectID: 2,
			completed: false
		},
		{
			todoID: 6,
			title: 'Events',
			projectID: 2,
			completed: false
		},
		{
			todoID: 7,
			title: 'Clan Event',
			projectID: 2,
			completed: false
		},
		{
			todoID: 8,
			title: 'Extra Earnings',
			projectID: 2,
			completed: false
		}
	];
	function addTodo() {
		todos = [
			...todos,
			{
				todoID: todos.length + 1,
				title: 'New Todo',
				projectID: 1,
				completed: false
			}
		];
	}
	async function removeTodo(todoID) {
		// Remove todo from list
		todos = todos.filter(todo => todo.todoID !== todoID);
	}
	function completeTodo(todoID){
		// Mark todo as completed
		todos = todos.map(todo => {
			if (todo.todoID === todoID) {
				todo.completed = true;
			}
			return todo;
		});
		openCongratsModal();
	}

	let congratsModalIsOpen = false;
	const openCongratsModal = () => ( congratsModalIsOpen = true);
	const closeCongratsModal = () => (congratsModalIsOpen = false);
</script>

<div class="Title">
	<h1>Exercise!</h1>
</div>

<div class="list">
	{#each todos as todo, index}
		<input
			style="font-family:Bradley Hand, cursive;background-color:cornflowerblue"
			bind:value={todos[index]}
		/>
		<label for="my-modal" class="btn modal-button" on:click={completeTodo(todo.todoID)}>Done</label>
		<br />
	{/each}
	<button on:click={addTodo}>Add</button>
</div>

<input type="checkbox" id="my-modal" class="modal-toggle" class:modal-open={congratsModalIsOpen} />
<div class="modal">
	<div class="modal-box">
		<h3 class="font-bold text-lg">Congratulations!</h3>
		<p class="py-4">You are one step closer to getting in shape!</p>
		<div class="modal-action">
			<label for="my-modal" class="btn" on:click={closeCongratsModal}>Yay!</label>
		</div>
	</div>
</div>

<footer>
	<h2>Get back into shape!</h2>
</footer>

<div class="Title">
	<h1>Archero</h1>
</div>

<div class="list">
	{#each todosa as todoa, index}
		<input bind:value={todosa[index]} />
		<button on:click={() => removeSelfa(index)}>Done</button>
		<br />
	{/each}
	<button on:click={addTodoa}>Add</button>
</div>

<style>
	.todos {
		font-size: 44;
	}
	.Title {
		text-align: center;
		display: block;
		margin: 20px auto;
		font-size: large;
	}
	.list {
		text-align: center;
		color: aqua;
	}
	button {
		color: white;

		background-color: red;
		border-radius: 2px;
		transition-duration: 0.4s;
	}
	button:hover {
		background-color: red;
		color: black;
	}
	footer {
		text-align: center;
		font-size: small;
	}
</style>
