<template>
  <q-layout view="hHh lpR fFf" class="shadow-11">
    <q-header elevated class="bg-purple text-white">
      <q-toolbar>
        <q-toolbar-title class="text-indigo-10">
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Discord finder
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',


  setup () {
    
  }
})
</script>

<style scoped>
p {
  color: hotpink;
}
</style>
