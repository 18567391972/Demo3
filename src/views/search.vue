<template>
	<div>
		 <van-search v-model="value" placeholder="请输入搜索关键词" @search="Search"/>
		 <van-tag type="primary" v-for="(item,index) in historyList" :key="index" style="margin-left: 15px;"
		  v-if="index <= 2"
		 >{{item}}</van-tag>
		 
		 <van-icon name="delete" @click="del"/>
	</div>
</template>

<script>
	export default {
		data(){
			return {
				value : '',
				historyList : []
			}
		},
		methods:{
			Search(){
				this.historyList.push(this.value)
				this.value = ''
				this.save();
			},
			save(){
				localStorage.historyList = JSON.stringify(this.historyList)
			},
			del(){
				this.historyList = []
				this.save();
			}
		},
		created() {
			let historyList = localStorage.historyList
			if(historyList){
				this.historyList = JSON.parse(historyList)
			}
		}
	}
</script>

<style scoped>
	
</style>
