<script>
  export default {
    data: () => ({
        title: "Elden Ring",
        drawer: false,
        group: null,
        items: [
            {
            title: 'Tutorial',
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

<v-navigation-drawer
    v-model="drawer"
    location="left"
    temporary
    color="transparent"
    elevation="0"
    :active="false"
    app
>
    <v-list>
        <v-list-item v-for="item in items" :title="item.title" :to="item.to">
            
        </v-list-item>
    </v-list>
</v-navigation-drawer>

</template>

<style scoped>
.app-bar{
    background-color: black;
}
</style>