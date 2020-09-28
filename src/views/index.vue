<template>
    <div>
        <van-search v-model="value" placeholder="请输入搜索关键词" @click="goto"/>
    </div>
</template>

<script>
    export default{
        data(){
            return {
				value : ''
            }
        },
		methods:{
			goto(){
				this.$router.push({
					path:'search'
				})
			}
		}
    }
</script>

<style scoped>
    
</style>