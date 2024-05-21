<template>
    <v-app>
      <v-layout class="layout-wrapper">
        <LeftMenu />
        <AppBar />
        <v-main class="main-container">
          <div class="main-wrapper">
            <h1>Good Morning, Doctor</h1>
            <v-tabs
              v-model="tabs"
              color="primary"
              grow
            >
              <v-tab
                :value="1"
              >
                <v-icon icon="mdi-pencil-circle-outline"></v-icon>
                Orders
              </v-tab>
              <v-tab
                :value="2"
              >
                <v-icon icon="mdi-signal-cellular-outline"></v-icon>
                Reports
              </v-tab>
            </v-tabs>

            <v-tabs-window v-model="tabs">
              <v-tabs-window-item
                v-for="i in 2"
                :key="i"
                :value="i"
              >
                <v-card>
                  <v-card-text>
                    <v-row gutters="12">
                      <v-col cols="12" sm="12" class="pb-0">
                        <h2>procedures</h2>
                      </v-col>
                      <v-col
                        v-for="n in ['Office Procedure', 'Biopsy /FNA', 'Day Procedure', 'Surgery']"
                        :key="n"
                        cols="12"
                        sm="3"
                      >
                      <v-card>
                        <p>{{n}}</p>
                        <v-icon icon="mdi mdi-chevron-right"></v-icon>
                      </v-card>
                      </v-col>
                    </v-row>
                    <!-- /// -->
                    <v-row gutters="12">
                      <v-col cols="12" sm="12" class="pb-0">
                        <h2>Labs</h2>
                      </v-col>
                      <v-col
                        v-for="n in ['Cath Labs', 'imaging', 'fuctional tests', 'Medications', 'Discharge', 'Consultation', 'Transfer']"
                        :key="n"
                        cols="12"
                        sm="3"
                      >
                      <v-card>
                        <p>{{n}}</p>
                        <v-icon icon="mdi mdi-chevron-right"></v-icon>
                      </v-card>
                      </v-col>
                    </v-row>
                    <!-- /// -->
                    <v-row gutters="12">
                      <v-col cols="12" sm="12" class="pb-0">
                        <h2>Therapy</h2>
                      </v-col>
                      <v-col
                        v-for="n in ['Occupational Therapy', 'Psychotherapy', 'beharioral therapy', 'respiratory therapy', 'Delivery', 'Admissions', 'Medical advice', 'Aqua Therapy']"
                        :key="n"
                        cols="12"
                        sm="3"
                      >
                      <v-card>
                        <p>{{n}}</p>
                        <v-icon icon="mdi mdi-chevron-right"></v-icon>
                      </v-card>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-card>
              </v-tabs-window-item>
            </v-tabs-window>
          </div>
        </v-main>
      </v-layout>
    </v-app>
  </template>
  
  <script>

  import LeftMenu from "@/components/AppDrawer.vue";
  import AppBar from "@/components/AppBar.vue";

  export default {
    components: {
      LeftMenu,
      AppBar
    },
    name: 'AppLayout',
    data: () => ({
      drawer: true,
      loaded: false,
      loading: false,
      tabs: null,
      items: [
        { text: 'Remainder for doctor', icon: 'mdi-bell' },
        { text: 'History', icon: 'mdi-account-multiple' },
        { text: 'pending consultation', icon: 'mdi-message-text' },
        { text: 'medication', icon: 'mdi-pill' },
        { text: 'pending report', icon: 'mdi-file' },
      ],
      pageLists: [
        { text: 'Dashboard', icon: 'mdi-view-dashboard' },
        { text: 'patient list', icon: 'mdi-account-multiple' },
        { text: 'Genaral File', icon: 'mdi-file-multiple' },
      ],
      activeItem: null,
    }),
    methods: {
      navigate(link) {
        this.$router.push(link);
      },
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