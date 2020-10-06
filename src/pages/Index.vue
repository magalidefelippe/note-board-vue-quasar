<template>
	<div class="q-pa-md q-gutter-sm">
		<q-editor v-model="editor" min-height="5rem" />

		<q-btn push color="primary" round icon="card_giftcard" />

		<q-card flat bordered>
		<q-card-section v-html="editor" />
		</q-card>
	</div>
</template>

<script>
export default {
	name: '',

	data: ()=>({
		editor: ''
	})
}
</script>
