
<template>
<div>
	<h1 class="Logo"> Vue api test </h1>
	<ul class="List">
		<li v-for="item in lists" v-text = "item.title"></li>
	</ul>
</div>
</template>

<script>
export default {
	data(){
		return {
			lists:[]
		}
	},
	created(){
		this.get_data()
	},
	methods:{
		get_data :function(params){
			if(!params) params = {};
			this.$http.get('https://cnodejs.org/api/v1/topics').then(function(response){
				this.lists = response.data.data;
				console.log(response.data.data)
			});
		}
	}
}
</script>

<style scoped>
.logo {color: red;}

.list {
  line-height: 2;
  li {border-bottom: 1px solid #ddd;}
}
</style>