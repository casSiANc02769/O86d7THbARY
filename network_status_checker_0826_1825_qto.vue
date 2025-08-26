// 代码生成时间: 2025-08-26 18:25:17
import { ref, onMounted, onUnmounted } from 'vue';

// Reactive data
const isConnected = ref(false);

// Network status checker function
function checkNetworkStatus() {
  isConnected.value = navigator.onLine;
}

// Lifecycle hooks
onMounted(() => {
  // Check network status when component mounts
  checkNetworkStatus();

  // Listen for online and offline events
  window.addEventListener('online', checkNetworkStatus);
  window.addEventListener('offline', checkNetworkStatus);
});

onUnmounted(() => {
  // Remove event listeners when component unmounts
  window.removeEventListener('online', checkNetworkStatus);
  window.removeEventListener('offline', checkNetworkStatus);
});
</script>

<style scoped>
/* Add component-specific styles here */
</style>
