<template>
    <v-navigation-drawer>
        <router-link to="" class="logo">
          <img :src="require('@/assets/images/logo.png')" alt="Logo" />
          OPD
        </router-link>
        <NavigationList :data="patientNavigationItems" />
        <NavigationList :data="pageLists" />
    </v-navigation-drawer>
</template>

<script>

import NavigationList from "@/components/Navigation";

  export default {
    components: {
      NavigationList
    },
    data: () => ({
        drawer: true,
        patientNavigationItems: [
            { text: 'Remainder for doctor', icon: 'mdi-bell' },
            { text: 'History', icon: 'mdi-account-multiple', className: 'adjust-width' },
            { text: 'pending consultation', icon: 'mdi-message-text', className: 'adjust-width' },
            { text: 'medication', icon: 'mdi-pill', className: 'adjust-width' },
            { text: 'pending report', icon: 'mdi-file', className: 'adjust-width' },
        ],
        pageLists: [
            { text: 'Dashboard', icon: 'mdi-view-dashboard' },
            { text: 'patient list', icon: 'mdi-account-multiple' },
            { text: 'Genaral File', icon: 'mdi-file-multiple' },
        ],
        activeItem: null,
    }),
    methods: {
      setActiveItem(item) {
        this.activeItem = item;
      },
      isActive(item) {
        return this.activeItem === item;
      },
      onClick () {
        this.loading = true
        setTimeout(() => {
          this.loading = false
          this.loaded = true
        }, 2000)
      },
    },
    created() {
      if (this.pageLists.length > 0) {
        this.activeItem = this.pageLists[0];
      }
    },
  }; 
  </script>
  
  <style scoped></style>