<template>
	<div class="row">
		<div class="col-md-6 col-md-offset-3">
			<div class="panel panel-default">
				<div class="panel-body">
					<div class="form-group">
						<input v-model="email" type="email" placeholder="Email"	class="form-control">
					</div>

					<div class="form-group">
						<input type="password" placeholder="Passwort" v-model="password"	class="form-control">
					</div>

					<button @click='login' class="btn btn-success pull-right">Login</button>
				</div>
			</div>
		</div>
	</div>
</template>


<script>
	export default {
		data () {
			return {
				email:'',
				password:''
			}
		},

		methods: {
			login() {
				var data = {
					client_id: 2,
					client_secret: 'PIeefNgL6UedwRjEjQzgQo1za1HOX0T91PaAiK1u',
					grant_type:'password',
					username: this.email,
					password: this.password
				}

				this.$http.post("oauth/token", data).then (function(response){
					this.$auth.setToken(response.body.access_token, response.body.expires_in + Date.now())
					this.$router.push("/feed")
				})
			}
		}
	}
</script>




<style>
	
</style>