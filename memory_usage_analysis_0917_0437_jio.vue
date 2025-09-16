// 代码生成时间: 2025-09-17 04:37:21
import { ref, onMounted, onUnmounted } from 'vue';

// 响应式数据
const memoryUsage = ref(0);
const intervalId = ref(null);

// 获取内存使用情况的函数
function getMemoryUsage() {
    const performance = window.performance;
    const memory = performance.memory;
    memoryUsage.value = (memory.usedJSHeapSize / memory.totalJSHeapSize) * 100;
}

// 生命周期钩子
onMounted(() => {
    // 监听内存使用情况
    intervalId.value = setInterval(getMemoryUsage, 1000);
});

onUnmounted(() => {
    // 清除定时器
    if (intervalId.value) {
        clearInterval(intervalId.value);
    }
});
</script>

<template>
  <div>
    <!-- 显示内存使用率 -->
    <h1>Memory Usage: {{ memoryUsage }}%</h1>
  </div>
</template>
