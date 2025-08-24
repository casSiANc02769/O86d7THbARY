// 代码生成时间: 2025-08-24 16:22:04
import { ref, onMounted, onUnmounted } from 'vue';

// 响应式数据: online status
const online = ref(true);

// 检测网络状态变化
const checkOnlineStatus = () => {
  online.value = navigator.onLine;
};

// 监听网络状态变化事件
const onNetworkStatusChange = () => {
  checkOnlineStatus();
};

// 在组件挂载时添加事件监听器
onMounted(() => {
  window.addEventListener('online', onNetworkStatusChange);
  window.addEventListener('offline', onNetworkStatusChange);
  checkOnlineStatus(); // 初始检查
});

// 在组件卸载时移除事件监听器
onUnmounted(() => {
  window.removeEventListener('online', onNetworkStatusChange);
  window.removeEventListener('offline', onNetworkStatusChange);
});

// 导出响应式数据供模板使用
# TODO: 优化性能
export { online };
</script>

<style scoped>
/* 样式内容 */
</style>
