<template>
	<div class="users">
		<h1>Users Info</h1>

		<div class="container">
			<form v-on:submit="addUser" class="form-inline">
				<div class="form-group">
					<label for="Name">Name</label>
					<input type="text" v-model="newUser.name" placeholder="Name" id="name">
				</div>
				<div class="form-group">
					<label for="email">Email</label>
					<input type="email" v-model="newUser.email" placeholder="Email" id="email">
				</div>
				<input type="submit" value="Submit" class="btn btn-primary">
			</form>
			<br><br>
			<table class="table table-bordered table-hover user_info">
			<thead>
				<tr>
					
					<th>Name</th>
					<th>Email</th>
					<th></th>
				</tr>
			</thead>
			<tbody>
				<tr  v-for="user in users">
					<td>{{user.name}}</td>
					<td>{{user.email}}</td>
					<td><button type="button" class="btn btn-info"v-on:click="deleteUser(user)">删除</button></td>
				</tr>
			</tbody>
		</table>
		</div>
		
	</div>
</template>

<script>
	export default {
		name:'users',
		data() {
			return {
				newUser:{},
				users:[
					{
						name:"Alice",
						email:"Alice@qq.com",
						contacted:false
					},
					{
						name:"May",
						email:"May@qq.com",
						contacted:false
					},
					{
						name:"Tina",
						email:"Tina@qq.com",
						contacted:false
					}
				]
			}
		},
		methods: {
			addUser(e) {
				this.users.push({
					name:this.newUser.name,
					email:this.newUser.email,
					contacted:false
				})
				e.preventDefault();
			},
			deleteUser(user){
				this.users.splice(this.users.indexOf(user),1)
			}
		}
	}
</script>

<style>
	.user_info th{
		text-align: center;
	}
	form input {
		padding-left: 10px;
	}
</style>