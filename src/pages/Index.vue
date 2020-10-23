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

		<q-card class="row" flat bordered v-for="(task, index) in tasks" :key="`task-${index}`">
			<q-card-section>
				<p v-if="task.state === false">Tarea incompleta</p>
				<p v-if="task.state === true">Tarea completa</p>
     		</q-card-section>

	  		<q-separator/>
				
			<q-card-section class="col" :class="[task.state ? 'do' : null]" v-html="task.content" />

  			<q-separator vertical />

			<q-card-actions vertical class="justify-around q-px-md">
				<q-btn flat round color="red" icon="delete_forever" >
					<q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
						Eliminar
					</q-tooltip>
				</q-btn>
				<q-btn @click="task.state = true" v-if="task.state === false" flat round color="accent" icon="check_circle_outline">
					<q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
						Tarea realizada
					</q-tooltip>
				</q-btn>
				<q-btn @click="task.state = false" v-if="task.state === true" flat round color="accent" icon="alarm">
					 <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
						Tarea incompleta
					 </q-tooltip>
				</q-btn>
       		</q-card-actions>
			
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

p{
	margin: 0;
}

.do{
	text-decoration: line-through;
}
</style>
