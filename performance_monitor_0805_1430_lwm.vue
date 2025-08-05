// 代码生成时间: 2025-08-05 14:30:18
import { ref, onMounted, onUnmounted } from 'vue';

// 响应式数据
const cpuUsage = ref(0);
const memoryUsage = ref(0);
const diskUsage = ref(0);

// 模拟性能数据
function fetchPerformanceData() {
    cpuUsage.value = Math.random() * 100;
    memoryUsage.value = Math.random() * 100;
    diskUsage.value = Math.random() * 100;
}

// 生命周期钩子
onMounted(() => {
    setInterval(fetchPerformanceData, 1000);
});

onUnmounted(() => {
    console.log('Component unmounted, stopping performance checks');
    // 这里可以清除定时器等资源
});

</script>

<template>
  <div class="performance-monitor">
    <h1>System Performance Monitor</h1>
    <div>CPU Usage: {{ cpuUsage }}%</div>
    <div>Memory Usage: {{ memoryUsage }}%</div>
    <div>Disk Usage: {{ diskUsage }}%</div>
  </div>
</template>

<style scoped>
.performance-monitor {
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-top: 20px;
}
</style>
