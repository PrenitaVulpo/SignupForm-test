<template>
  <form @submit.prevent="handleSubmit">
		<label for="email">E-mail</label>
		<input type="email" name="email" required v-model="email"/>

		<label for="password">Password</label>
		<input type="password" name="password" required v-model="password"/>
		<div v-if="passwordError" class="error">{{ passwordError }}</div>

		<label for="role">Role</label>
		<select v-model="role">
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>

		<label for="skills">Skills</label>
		<input type="text" v-model="tempSkill" @keyup="addSkill"/>
		<div v-for="skill in skills" :key="skill" class="pill">
			<span @click="deleteSkill(skill)">{{ skill }}</span>
		</div>

		<div class="terms">
			<input type="checkbox" required v-model="terms"/>
			<label for="terms">Accept terms and conditions</label>
		</div>

		<div class="submit">
			<button>Creante an account</button>
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
			role: 'developer',
			terms: false,
			tempSkill: '',
			skills: [],
			passwordError: '',
		}
	},
	methods: {
		addSkill(e) {
			if (e.key === "Enter" && this.tempSkill) {
				if (!this.skills.includes(this.tempSkill)) {	
					this.skills.push(this.tempSkill)
				}
				this.tempSkill = ''
			}
		},
		deleteSkill(skill) {
			this.skills = this.skills.filter(item => {return skill !== item})
		},
		handleSubmit(){
			this.passwordError = this.password.length > 6 ? '' 
				: 'the password must contain at least 6 caracters'
			
			if (!this.passwordError) {
				console.log({
					email: this.email,
					password: this.password,
					role: this.role,
					skills: this.skills,
				})
			}
		}
	}
}
</script>

<style>
	form {
		max-width: 420px;
		margin: 30px auto;
		background: #fff;
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
	.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
	button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: #fff;
    border-radius: 20px;
  }
  .submit {
    text-align: center;
  }
  .error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }
</style>
