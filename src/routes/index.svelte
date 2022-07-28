<script>
	let todos = ['30 situps', '20 pushups', '5 pull ups'];
	function addTodo() {
		todos = [...todos, ''];
	}
	function removeSelf(index) {
		todos = [...todos.slice(0, index), ...todos.slice(index + 1)];
	}
    let todosa = ['Dailies', '5 Bosses', 'Events', 'Clan Event', 'Extra Earnings'];
	function addTodoa() {
		todosa = [...todosa, ''];
	}
	function removeSelfa(index) {
		todosa = [...todosa.slice(0, index), ...todosa.slice(index + 1)];
	}
</script>

<div class="Title">
	<h1>Exercise!</h1>
</div>

<div class="list">
	{#each todos as todo, index}
		<input style="font-family:Bradley Hand, cursive;background-color:cornflowerblue" bind:value={todos[index]} />
		<label for="my-modal" class="btn modal-button" on:click ={removeSelf(index)}>Done</label>
		<br />
	{/each}
	<button on:click={addTodo}>Add</button>
</div>

<input type="checkbox" id="my-modal" class="modal-toggle" />
<div class="modal">
  <div class="modal-box">
    <h3 class="font-bold text-lg">Congratulations!</h3>
    <p class="py-4">You are one step closer to getting in shape!</p>
    <div class="modal-action">
      <label for="my-modal" class="btn">Yay!</label>
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
