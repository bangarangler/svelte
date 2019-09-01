<script>
	let name = 'Jon';
	let age = 31;

	$: uppercaseName = name.toUpperCase();

	function incrementAge() {
		age = age += 1;
	}

	function changeName() {
		name = 'Jonathan';
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
<button on:click={changeName}>Change Name</button>
