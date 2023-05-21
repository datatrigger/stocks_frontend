<script setup lang="js">
    
    import Chart from 'chart.js/auto'
    import { ref, onMounted } from 'vue'

    const results = ref(null);
    const res = await fetch("https://stocks-backend-2peshcrm3a-oa.a.run.app/data");
    results.value = await res.json();
    
    onMounted( () => { 

        new Chart(
            document.getElementById("myChart"), 
            {
                type: 'line',
                data: results.value,
                options: {
                    title: {
                        display: true,
                        text: 'Performance of 3 Big Tech stocks over the last 10 business days'
                    }
                }
            })

    })
    
</script>

<template>
    <h2>Performance of 3 Big Tech stocks over the last 10 business days</h2>
    <h3><i>Refresh the page to get live updates</i></h3>
    <div>
        <canvas id="myChart"></canvas>
    </div>
</template>

