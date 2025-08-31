// 代码生成时间: 2025-09-01 03:39:46
import { ref, onMounted, onUnmounted } from 'vue';

// 响应式数据
const message = ref('Hello, Vue 3!');
const counter = ref(0);

// 方法
function incrementCounter() {
  counter.value += 1;
}

// 生命周期钩子
onMounted(() => {
  console.log('Component is mounted.');
});

onUnmounted(() => {
  console.log('Component is unmounted.');
});

</script>

<style scoped>
/* Add your styles here */
</style>