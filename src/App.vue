<script >

export default {
  data: () => ({
    title: "Elden Ring",
    drawer: false,
    group: null,
    items: [
        {
        title: 'Resume',
        value: 'foo',
        to: '/',
        },
        {
        title: 'Settings',
        value: 'bar',
        to: '/about'
        },

    ],
  }),

  watch: {
    group () {
      this.drawer = false
    },
  },
  methods: {
      redirectToHome() {
          this.$router.push({ path: '/' });
      },
  }
}
</script>

<template>
  <v-app style="background-color: #181818; color: white;">
    <v-main>
      <v-btn style="position: absolute;
        top: 10px;
        text-align: center;
        z-index: 100;
        display:block;"
        size="small" 
        icon="mdi-menu" 
        variant="text" 
        color="white" 
        @click.stop="drawer = !drawer">
      </v-btn>
      <v-navigation-drawer
          v-model="drawer"
          location="bottom"
          temporary
          color="transparent"
          elevation="0"
          :active="false"
          app
      >
          <v-list>
              <v-list-item class="mt-5" v-for="item in items" :title="item.title" :to="item.to">
                  
              </v-list-item>
          </v-list>
      </v-navigation-drawer>
      <router-view></router-view>

    </v-main>
  </v-app>

</template>

<style scoped>

</style>
