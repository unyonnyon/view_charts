<template>
    <div class="home">
        <p>home</p>
        <viewer :json="jsonText" />
    </div>
</template>

<script>
// @ is an alias to /src
import Viewer from "../components/ViewChart.vue";

export default {
    name: "Home",
    components: {
        Viewer
    },
    data: () => ({
        jsonText: ""
    })
};
</script>
