<template>
  <div class="flex-container" :style="resultStyles">
		<div
		  v-for="(item, index) in flexElement"
		  :key="index"
		  :class="item"
			class="flex-element">
			{{ index+1 }}
		</div>
	</div>
	<ul class="select-container">
		<li>
			<p>Justify Content:</p>
			<SelectVue :select="JUSTIFYCONTENT" @emit-value="handleJustifyContent" />
		</li>
		<li>
			<p>Align Items:</p>
			<SelectVue :select="ALIGNITEMS" @emit-value="handleAlignItems" />
		</li>
		<li>
			<p>Flex Wrap:</p>
			<SelectVue :select="FLEXWRAP" @emit-value="handleWrap" />
		</li>
		<li>
			<p>Flex Direction:</p>
			<SelectVue :select="FLEXDIRECTION" @emit-value="handleDirection" />
		</li>
	</ul>
</template>

<script setup>
	import { ref, computed } from 'vue'
	import { JUSTIFYCONTENT, ALIGNITEMS, FLEXWRAP, FLEXDIRECTION } from './constans.js'
	import SelectVue from './components/SelectVue.vue'
	const flexElement = ['red', 'yellow', 'green', 'blue', 'violet']

	const currentJustifyContent = ref('flex-start')
	const currentAlignItems = ref('flex-start')
	const currentWrap = ref('nowrap')
	const currentDirection = ref('row')

	const handleJustifyContent = (value) => {
		currentJustifyContent.value = value
	}
	const handleAlignItems = (value) => {
		currentAlignItems.value = value
	}
	const handleWrap = (value) => {
		currentWrap.value = value
	}
	const handleDirection = (value) => {
		currentDirection.value = value
	}

	const result = computed(() => {
		return [
			{ value: `justify-content: ${currentJustifyContent.value};` },
			{ value: `align-items: ${currentAlignItems.value};` },
			{ value: `flex-wrap: ${currentWrap.value};` },
			{ value: `flex-direction: ${currentDirection.value};` },
		]
	})

	const resultStyles = computed(() => {
		return [
		result.value[0].value, result.value[1].value, result.value[2].value, result.value[3].value
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

