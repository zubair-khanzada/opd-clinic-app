<template>
    <v-app-bar class="app-bar">
        <div class="app-wrapper">
            <v-text-field
                :loading="loading"
                append-inner-icon="mdi-magnify"
                density="compact"
                label="Search"
                variant="solo"
                hide-details
                single-line
                @click:append-inner="onClick"
            ></v-text-field>
            <div class="d-flex align-center">
                <v-btn
                class="appointments"
                >
                Appointments
                </v-btn>
                <v-btn class="ml-2 mr-2" icon="mdi-bell-outline" size="large"></v-btn>
                <img :src="require('@/assets/images/user-avatar.png')" alt="Avatar" />
            </div>
        </div>
    </v-app-bar>
</template>

<script>

  export default {
    data: () => ({
      loaded: false,
      loading: false,
    }),
    methods: {
      onClick () {
        this.loading = true
        setTimeout(() => {
          this.loading = false
          this.loaded = true
        }, 2000)
      },
    },
  };
  
  </script>
  
  <style scoped></style>