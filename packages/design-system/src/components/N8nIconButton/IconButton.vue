<template functional>
	<component :is="$options.components.N8nButton"
		:type="props.type"
		:disabled="props.disabled"
		:size="props.size === 'xlarge' ? 'large' : props.size"
		:loading="props.loading"
		:title="props.title"
		:icon="props.icon"
		:iconSize="$options.iconSizeMap[props.size] || props.size"
		:theme="props.theme"
		@click="(e) => listeners.click && listeners.click(e)"
		circle
	/>
</template>

<script lang="ts">
import N8nButton from '../N8nButton';

const iconSizeMap = {
	large: 'medium',
	xlarge: 'large',
};

export default {
	name: 'n8n-icon-button',
	components: {
		N8nButton,
	},
	props: {
		type: {
			type: String,
		},
		title: {
			type: String,
		},
		size: {
			type: String,
			default: 'medium',
			validator: (value: string): boolean =>
				['small', 'medium', 'large', 'xlarge'].indexOf(value) !== -1,
		},
		loading: {
			type: Boolean,
			default: false,
		},
		disabled: {
			type: Boolean,
			default: false,
		},
		icon: {
			type: String,
			required: true,
		},
		theme: {
			type: String,
		},
	},
	iconSizeMap,
};
</script>
