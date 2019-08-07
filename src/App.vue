<template>
  <v-app>
    <Sidebar/>
    <Header/>
    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
  import Sidebar from './layouts/Sidebar.vue'
  import Header from './layouts/Header.vue'
export default {
  name: 'App',
  data: () => ({
    //
  }),
  components: {
    Sidebar,
    Header
  }
};
</script>
