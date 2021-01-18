<template>
	<div id="app">
	<Header msg="Welcome to Horseracing!"/>
	<Game />
	</div>
</template>

<script>
import Header from './components/Header.vue'

export default {
	name: 'App',
	components: {
	Header,
	}
}
</script>

<style>
body, html {
	background-color: #22303f;
}

#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #ffffff;
	margin-top: 60px;
	background-color: #22303f;
}
</style>
