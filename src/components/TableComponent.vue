<script setup lang="js">
    
    import { ref } from 'vue'

    const results = ref(null);
    const response = await fetch("https://stocks-backend-2peshcrm3a-oa.a.run.app/metrics");
    if (!response.ok) {
        const message = `An error has occured: ${response.status}`;
        throw new Error(message);
    }
    results.value = await response.json();

</script>

<template>
    <h2>Metrics computed over the last 10 business days</h2>
    <ol>
        <div v-for="item in results.metrics">
            {{ item }}
        </div>
    </ol>
</template>
