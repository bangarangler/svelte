<script>
	let name = 'Jon';
	let age = 31;

	function incrementAge() {
		age = age += 1;
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
