<template>
  <div class="flex-container" :style="[result[0].value, result[1].value]">
		<div
		  v-for="item in flexElement"
		  :key="item"
		  :class="item"
			class="flex-element">
			{{ item }}
		</div>
	</div>
	<div>
		<SelectVue :select="JUSTIFYCONTENT" @emit-value="handleJustifyContent"/>
		<SelectVue :select="ALIGNITEMS" @emit-value="handleAlignItems"/>
	</div>
</template>

<script setup>
	import { ref, computed } from 'vue'
	import { JUSTIFYCONTENT, ALIGNITEMS } from './constans.js'
	import SelectVue from './components/SelectVue.vue'
	const flexElement = ['red', 'yellow', 'green', 'blue', 'violet']

	const currentJustifyContent = ref('flex-start')
	const currentAlignItems = ref('flex-start')

	const handleJustifyContent = (value) => {
		currentJustifyContent.value = value
	}
	const handleAlignItems = (value) => {
		currentAlignItems.value = value
	}

	const result = computed(() => {
		return [
		{ value: `justify-content: ${currentJustifyContent.value};` },
		{ value: `align-items: ${currentAlignItems.value};` }
		]
	})
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

