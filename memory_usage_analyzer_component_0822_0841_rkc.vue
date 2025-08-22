// 代码生成时间: 2025-08-22 08:41:09
import { ref, onMounted, onUnmounted } from 'vue';
import { getMemoryUsage } from './memoryService'; // 假设这是一个获取内存使用情况的服务

// 响应式数据，存储内存使用情况
const memoryUsageInMB = ref(0);

// 在组件挂载时获取内存使用情况
onMounted(() => {
  startMemoryUsageAnalysis();
});

// 在组件卸载时停止内存使用分析
onUnmounted(() => {
  stopMemoryUsageAnalysis();
});

let memoryAnalysisInterval = null;

// 获取内存使用情况的函数
function startMemoryUsageAnalysis() {
  if (memoryAnalysisInterval) {
    clearInterval(memoryAnalysisInterval);
  }
  memoryAnalysisInterval = setInterval(() => {
    getMemoryUsage().then(data => {
      memoryUsageInMB.value = data;
    });
  }, 1000); // 每秒钟更新一次内存使用情况
}

// 停止内存使用分析的函数
function stopMemoryUsageAnalysis() {
  if (memoryAnalysisInterval) {
    clearInterval(memoryAnalysisInterval);
    memoryAnalysisInterval = null;
  }
}
</script>

<style scoped>
/* 组件的样式 */
</style>
