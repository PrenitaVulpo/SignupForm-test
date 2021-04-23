<template>
  <form>
		<label for="email">E-mail</label>
		<input type="email" name="email" required v-model="email"/>

		<label for="password">Password</label>
		<input type="password" name="password" required v-model="password"/>

		<label for="password">Role</label>
		<select name="role">
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>

		<div class="terms">
			<input type="checkbox" required v-model="terms"/>
			<label for="terms">Accept terms and conditions</label>
		</div>
	</form>

	<p>E-mail: {{ email }}</p>
	<p>Password: {{ password }}</p>
	<p>Role: {{ role }}</p>
	<p>Terms Accepted?: {{ terms }}</p>
</template>

<script>
export default {
	data() {
		return {
			email: '',
			password: '',
			role: '',
			terms: false,
		}
	}
}
</script>

<style>
	form {
		max-width: 420px;
		margin: 30px auto;
		background: white;
		text-align: left;
		padding: 40px;
		border-radius: 10px;
	}
	label {
		color: #aaa;
		display: inline-block;
		margin: 25px 0 15px;
		font-size: 0.6em;
		text-transform: uppercase;
		letter-spacing: 1px;
		font-weight: bold;
	}
	input, select {
		display: block;
		padding: 10px 6px;
		width: 100%;
		box-sizing: border-box;
		border: none;
		border-bottom: 1px solid #ddd;
		color: #555;
	}
	input[type="checkbox"] {
		display: inline-block;
		width: 16px;
		margin: 0 10px 0 0;
		position: relative;
		top: 2px;
	}
</style>
