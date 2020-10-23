<template>
	<div class="q-pa-md q-gutter-sm">
		
		<q-editor
			v-model="editor"
			:definitions="{
				save: {
				tip: 'Guardar nota',
				icon: 'save',
				label: 'Guardar',
				handler: saveWork
				},
			}"
			:toolbar="[
				['bold', 'italic', 'strike', 'underline'], [ 'save']
			]"
			/>

		<q-card flat bordered>		
			<q-card-section v-html="editor" />
		</q-card>

	</div>
</template>

<script>
export default {
	name: '',

	data: () => ({
		editor: '',
		note_collection: [],
	}),

	methods: {
		saveWork(){
			//this.note_collection.push({content: this.editor})
			 this.$q.notify({
        		message: 'Saved your text to local storage',
        		color: 'green-4',
        		textColor: 'white',
        		icon: 'cloud_done'
     		})
		}
	}
}
</script>
