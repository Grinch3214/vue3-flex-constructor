<template>
  <div class="flex-container">
		<div
		  v-for="item in flexElement"
		  :key="item"
		  :class="item"
			class="flex-element">
			{{ item }}
		</div>
	</div>
</template>

<script setup>
	const flexElement = ['red', 'yellow', 'green', 'blue', 'violet']
</script>

<style lang="scss">
@font-face {
	font-family: 'Open Sans';
	src: url('./assets/fonts/OpenSans-Regular.woff2') format('woff2');
	font-weight: 400;
	font-style: normal;
	font-display: swap;
}

@font-face {
	font-family: 'Open Sans';
	src: url('./assets/fonts/OpenSans-SemiBold.woff2') format('woff2');
	font-weight: 600;
	font-style: normal;
	font-display: swap;
}

@font-face {
	font-family: 'Open Sans';
	src: url('./assets/fonts/OpenSans-ExtraBold.woff2') format('woff2');
	font-weight: 800;
	font-style: normal;
	font-display: swap;
}
</style>

