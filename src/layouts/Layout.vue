<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="absolute-center">
          To Do
        </q-toolbar-title>

      </q-toolbar>
    </q-header>
    <q-footer elevated>
      <q-tabs>
        <q-route-tab 
            v-for="nav in navs"
            :key="nav.label"
            :to="nav.to"
            :icon="nav.icon" 
            :label="nav.label" >
        </q-route-tab>
      </q-tabs>
    </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      :breakpoint="767" 
      :width="250"
      bordered
      content-class="bg-indigo-1"
    >
      <q-list>
        <q-item-label header>Navigation</q-item-label>

        <q-item 
            v-for="nav in navs"
            :key="nav.label"
            :to="nav.to"
            exact
            clickable >
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar';

export default {
  name: 'MyLayout',
  data() {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      navs:[
          {
              label: 'Todo',
              icon: 'list',
              to: '/'
          },
          {
              label: 'Settings',
              icon: 'settings',
              to: '/settings'
          },
          {
              label: 'There',
              icon: 'settings',
              to: '/there'
          },
      ]
    };
  },
  methods: {
    openURL,
  },
};
</script>

<style lang="scss">
    @media screen and (min-width:768px){
        .q-footer{
            display:none;
        }        
    }
</style>
