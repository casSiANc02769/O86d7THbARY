// 代码生成时间: 2025-09-08 02:17:38
import { ref, onMounted, onUnmounted } from 'vue';

// 响应式数据
const tasks = ref([]);
const taskName = ref('');

// 添加任务
function addTask() {
    if (!taskName.value) return;
    const newTask = {
        id: Date.now(),
        name: taskName.value
    };
    tasks.value.push(newTask);
    taskName.value = '';
}

// 定时任务调度器
let timer;
function scheduleTask() {
    // 例如，每5秒执行一次任务
    timer = setInterval(() => {
        console.log('定时任务执行中...');
    }, 5000);
}

// 生命周期钩子
onMounted(() => {
    scheduleTask();
});

onUnmounted(() => {
    if (timer) {
        clearInterval(timer);
    }
});
</script>

<style scoped>
/* 样式内容 */
</style>