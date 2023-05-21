<script setup lang="js">
    
    import { ref } from 'vue'

    const results = ref(null);
    const res = await fetch("https://stocks-backend-2peshcrm3a-oa.a.run.app/metrics");
    results.value = await res.json();

</script>

<template>
    <h2>Metrics computed over the last 10 business days</h2>
    <ol>
        <div v-for="item in results.metrics">
            {{ item }}
        </div>
    </ol>
</template>
