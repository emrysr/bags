<script setup lang="ts">
import { ref } from "vue";
const html = ref();
const status = ref("Ready");
function loadData() {
    status.value = "Loading...";
    var url =
        "https://docs.google.com/spreadsheet/pub?key=p_aHW5nOrj0VO2ZHTRRtqTQ&single=true&gid=0&range=A1&output=csv";
    const xmlhttp = new XMLHttpRequest();
    xmlhttp.onreadystatechange = function () {
        if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
            html.value = xmlhttp.responseText;
        }
    };
    xmlhttp.open("GET", url, true);
    xmlhttp.send(null);
}
</script>

<template>
    <pre v-text="status"></pre>
    <button type="button" @click="loadData">Load Spreadsheet Data</button>
    <div id="display"></div>
</template>

<style scoped>
.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
}
.logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
