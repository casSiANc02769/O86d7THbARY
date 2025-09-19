// 代码生成时间: 2025-09-20 02:02:28
import { onMounted, ref } from 'vue';

// 响应式数据
const cpuUsage = ref(0);
const memoryUsage = ref(0);
const diskUsage = ref(0);

// 模拟获取系统性能数据
function fetchSystemPerformanceData() {
  // 此处应有实际的API调用，这里使用模拟数据
  cpuUsage.value = Math.floor(Math.random() * 100);
  memoryUsage.value = Math.floor(Math.random() * 100);
  diskUsage.value = Math.floor(Math.random() * 100);
}

// 生命周期钩子：组件挂载后获取数据
onMounted(() => {
  fetchSystemPerformanceData();
  setInterval(fetchSystemPerformanceData, 1000);
});
</script>

<style scoped>
.performance-monitor {
  padding: 20px;
  background-color: #f0f0f0;
  border-radius: 5px;
}
</style>