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

		<q-card flat bordered v-for="task in tasks" :key="`task-${task.content}`">		
			<q-card-section :class="[task.state ? complete_class : false, incomplete_class]"  v-html="task.content" />
		</q-card>

	</div>
</template>

<script>
export default {
	name: '',

	data: () => ({
		editor: '',
		tasks: [],
		complete_class: '',
		incomplete_class: 'task_incomplete'
	}),

	methods: {
		saveWork(){
			if(this.editor === ''){
				this.$q.notify({
        		message: 'Error, la tarea está vacia',
        		color: 'red-8',
        		textColor: 'white',
        		icon: 'error_outline'
     		})
			}
			else{
				this.tasks.push({content: this.editor, state: false});
				this.editor = '';
				this.$q.notify({
					message: 'Tarea guardada',
					color: 'green-4',
					textColor: 'white',
					icon: 'cloud_done'
				})
			 }
		}
	}
}
</script>

<style  scoped>
.task_incomplete{
	background: rgb(241, 195, 195);
}
</style>
