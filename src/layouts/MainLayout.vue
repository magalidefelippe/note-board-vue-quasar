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
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title class="text-grey-9">
          Tareas windows
        </q-toolbar-title>

    
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-purple-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-9"
        >
          Menú
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Pendientes',
    icon: 'school',
    link: '/'
  },
 
];

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
