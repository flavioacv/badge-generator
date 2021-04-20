<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar style="height: 70px">
        <q-toolbar-title>
          Badge Generator
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container class="bg-dark">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  data () {
    return {
    }
  }
}
</script>
