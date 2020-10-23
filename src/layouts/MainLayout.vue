<template>
	<q-layout view="lHh Lpr lFf">

		<q-header elevated class="bg-purple-1"> 
			<q-toolbar>
				<q-btn
					flat
					dense
					round
					class="text-grey-9"
					icon="menu"
					@click="leftDrawerOpen = !leftDrawerOpen"/>

				<q-toolbar-title class="text-grey-9">
					Tareas
				</q-toolbar-title>
			</q-toolbar>
		</q-header>

		<q-drawer
			v-model="leftDrawerOpen"
			show-if-above
			bordered
			content-class="bg-purple-1">
				<q-list>
					<EssentialLink
						v-for="link in essentialLinks"
						:key="link.title"
						v-bind="link"/>
				</q-list>
		</q-drawer>

		<q-page-container>
			<router-view/>
		</q-page-container>

	</q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue';

const linksData = [
  {
    title: 'Pendientes',
    icon: 'school',
    link: '/'
  },
];

export default {
	name: 'MainLayout',
	
	data: () => ({
		leftDrawerOpen: false,
		essentialLinks: linksData
	}),

	components: { EssentialLink }
}
</script>
