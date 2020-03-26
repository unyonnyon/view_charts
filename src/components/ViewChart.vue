<template>
    <v-card dark>
        <p>view chart</p>
        <chart v-if="isLoaded" :chart-data="datacollection" :options="options" />
    </v-card>
</template>

<script>
import Chart from "./LineChart.vue";

export default {
    components: {
        Chart
    },
    props: {
        json: {
            type: String,
            required: true,
            default() {
                return "";
            }
        }
    },
    data: () => ({
        isLoaded: false,
        datacollection: null,
        options: {
            responsive: true,
            maintainAspectRatio: false
        }
    }),
    methods: {
        createDataCollection() {
            if (this.isLoaded) return;
            const data = JSON.parse(this.json);

            if (data.length < 1) return;
            const labels = Object.keys(data[0]);

            if (labels.length < 1) return;
            const datasets = [];

            for (const label of labels) {
                const dataObject = {
                    label: label,
                    type: "line",
                    data: [...data].map(v => v[label])
                };
                datasets.push(dataObject);
            }

            this.datacollection = {
                labels: labels,
                datasets: datasets
            };

            this.isLoaded = true;
        }
    },
    watch: {
        json() {
            this.createDataCollection();
        }
    }
};
</script>

<style>
</style>