// 代码生成时间: 2025-09-17 08:46:44
import { ref, onMounted, onUnmounted } from 'vue';

export default {
  name: 'RandomNumberGenerator',
  setup() {
    // 响应式数据
    const number = ref(0);
    const randomNumber = ref(0);

    // 生成随机数函数
    function generateRandomNumber() {
      if (number.value > 0) {
        randomNumber.value = Math.floor(Math.random() * number.value) + 1;
      } else {
        randomNumber.value = Math.floor(Math.random() * 100) + 1;
      }
    }

    // 响应式数据
    const min = ref(1);
    const max = ref(100);

    // 生命周期钩子
    onMounted(() => {
      console.log('RandomNumberGenerator 组件已挂载');
    });

    onUnmounted(() => {
      console.log('RandomNumberGenerator 组件已卸载');
    });

    return {
      number,
      randomNumber,
      generateRandomNumber,
    };
  },
};
</script>

<style scoped>
/* 组件样式 */
</style>
