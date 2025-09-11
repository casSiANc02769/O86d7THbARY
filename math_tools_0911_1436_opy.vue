// 代码生成时间: 2025-09-11 14:36:00
import { ref, onMounted } from 'vue';

// Reactive state
const num1 = ref(0);
const num2 = ref(0);
const result = ref(0);

// Methods
function add() {
  result.value = num1.value + num2.value;
}

function subtract() {
  result.value = num1.value - num2.value;
}

function multiply() {
  result.value = num1.value * num2.value;
}

function divide() {
  if (num2.value === 0) {
    alert('Cannot divide by zero!');
    return;
  }
  result.value = num1.value / num2.value;
}

//生命周期钩子
onMounted(() => {
  console.log('Math Tools component is mounted.');
});
</script>

<style scoped>
/* Add your styles here */
</style>
