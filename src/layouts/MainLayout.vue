<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label header class="text-grey-8">
          Navigation
        </q-item-label>
        <AppLink v-for="link in appLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import AppLink from 'components/AppLink.vue';

const linksData = [
  {
    title: 'Oeuvres',
    caption: 'Liste des oeuvres lues',
    icon: 'local_library',
    link: '/'
  },
  {
    title: 'Prochaine Rencontre',
    caption: 'Informations sur la prochaine rencontre',
    icon: 'connect_without_contact',
    link: '/ProchaineRencontre'
  }
];

import { Vue, Component } from 'vue-property-decorator';

@Component({
  components: { AppLink }
})
export default class MainLayout extends Vue {
  leftDrawerOpen = false;
  appLinks = linksData;
}
</script>
