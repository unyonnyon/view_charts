<template>
    <v-app>
        <v-app-bar app color="lime" dark>
            <v-spacer></v-spacer>
        </v-app-bar>

        <v-content>
            <router-view></router-view>
        </v-content>
    </v-app>
</template>

<script>
export default {
    name: "App",

    data: () => ({
        //
    })
};
</script>
