<template>
  <q-layout view="hHh lpR fff">
    <q-header reveal bordered class="bg-white text-black">
      <q-toolbar>
        <q-toolbar-title>
          <q-icon name="fa fa-flask" />
          Experimentation Platform
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {};
  },
};
</script>
