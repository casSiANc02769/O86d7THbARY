// 代码生成时间: 2025-09-12 02:29:50
import { ref, onUnmounted, onMounted } from 'vue';

// 响应式数据，存储错误日志
const errorLogs = ref([]);

// 组件挂载时注册全局错误监听
onMounted(() => {
  window.addEventListener('error', (event) => {
    errorLogs.value.push({
      message: event.message,
      filename: event.filename,
      lineno: event.lineno,
      colno: event.colno,
      error: event.error
    });
  });
});

// 组件卸载时移除全局错误监听
onUnmounted(() => {
  window.removeEventListener('error', (event) => {
    errorLogs.value.push({
      message: event.message,
      filename: event.filename,
      lineno: event.lineno,
      colno: event.colno,
      error: event.error
    });
  });
});

</script>

<template>
  <div class="error-logger">
    <h2>Error Logs</h2>
    <ul v-if="errorLogs.length > 0">
      <li v-for="(log, index) in errorLogs" :key="index">{{ log.message }} at {{ log.filename }}:{{ log.lineno }}:{{ log.colno }}</li>
    </ul>
    <p v-else>No errors logged.</p>
  </div>
</template>

<style>
.error-logger {
  padding: 20px;
  border: 1px solid #ddd;
}
</style>
