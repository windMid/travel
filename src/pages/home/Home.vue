<template>
	<div>
		<HomeHeader></HomeHeader>
		<router-view/>
	</div>
</template>

<script>
import HomeHeader from './components/Header.vue'
export default {
	name: "Home",
	components:{
		HomeHeader
	}
}
</script>

<style>
	
</style>