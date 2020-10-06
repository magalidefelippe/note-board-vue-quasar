<template>
	<div class="q-pa-md q-gutter-sm">
		<div>
		<q-btn class="float-right q-my-sm" @click="alert = true" push color="primary" round icon="note_add" />
		
		<q-dialog v-model="alert">
			<q-card flat bordered>
				 <q-card-section>
			<q-editor 
				v-model="editor" 
				min-height="5rem"
				
				:toolbar="[
							[
							{
								label:'Alinear',
								icon: $q.iconSet.editor.align,
								fixedLabel: true,
								list: 'only-icons',
								options: ['left', 'center', 'right', 'justify']
							},
							],

							['bold', 'italic', 'strike', 'underline'],
					
							[
							{
								label: 'Tamaño del texto',
								icon: $q.iconSet.editor.fontSize,
								fixedLabel: true,
								fixedIcon: true,
								list: 'no-icons',
								options:[
											'size-1',
											'size-2',
											'size-3',
											'size-4',
											'size-5',
											'size-6',
											'size-7'
										]
							},
							{
								label: 'Fuente',
								icon: $q.iconSet.editor.font,
								fixedIcon: true,
								list: 'no-icons',
								options: [
											'default_font',
											'arial',
											'arial_black',
											'comic_sans',
											'courier_new',
											'impact',
											'lucida_grande',
											'times_new_roman',
											'verdana'
										]
							}],

							['undo', 'redo'],
						]"
				:fonts="{
							arial: 'Arial',
							arial_black: 'Arial Black',
							comic_sans: 'Comic Sans MS',
							courier_new: 'Courier New',
							impact: 'Impact',
							lucida_grande: 'Lucida Grande',
							times_new_roman: 'Times New Roman',
							verdana: 'Verdana'
						}"/>
				 </q-card-section>
				  <q-card-actions align="right">
          <q-btn @click="saveNote" v-close-popup flat color="primary" round icon="event" />
        </q-card-actions>
			</q-card>
		<!-- <q-card-section v-html="editor" /> -->
	
		 </q-dialog>
		</div>

		<div class="q-mx-xl" v-if="note_collection != []">
			
		 <q-card v-for="(note, id) in note_collection"
		 	:key="`note-${id}`">
			 <q-card-section v-html="note.content" />
		 </q-card>
		</div>
	</div>
</template>

<script>
export default {
	name: '',

	data: ()=>({
		editor: '',
		note_collection: [],
		alert: false
	}),

	methods: {
		saveNote(){
			this.note_collection.push({content: this.editor})
		}
	}
}
</script>
