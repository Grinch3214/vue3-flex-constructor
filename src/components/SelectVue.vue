<template>
	<select @change="handleSelectChange($event.target.value)">
		<option v-for="item in select" :key="item.value" :value="item.value">{{ item.name }}</option>
	</select>
</template>

<script setup>
	const props = defineProps({
		select: {
			type: Array,
			required: true
		}
	})

	const emits = defineEmits(['emitValue'])

	const handleSelectChange = (value) => {
		emits('emitValue', value);
	}
</script>