// 代码生成时间: 2025-09-14 04:55:46
import { ref, onMounted, computed } from 'vue';

// 响应式数据
const inputValue = ref('');
const hashValue = ref(null);

// 计算哈希的函数，这里以简单的哈希作为示例
function calculateHashSimple(input) {
  let hash = 0;
  for (let i = 0; i < input.length; i++) {
    const char = input.charCodeAt(i);
    hash = (hash << 5) - hash + char;
    hash |= 0;
  }
  return hash;
}

// 计算哈希值的函数
function calculateHash() {
  hashValue.value = calculateHashSimple(inputValue.value).toString();
}

// 计算属性，用于响应inputValue的变化
const computedHash = computed(() => calculateHashSimple(inputValue.value).toString());

// 生命周期钩子
onMounted(() => {
  console.log('Component mounted');
});

// 监听计算属性的变化，并更新hashValue
watch(computedHash, (newValue) => {
  hashValue.value = newValue;
});
</script>

<style scoped>
.hash-calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

input {
  width: 300px;
  padding: 10px;
  margin-bottom: 10px;
}

button {
  padding: 10px 20px;
  margin-top: 5px;
  cursor: pointer;
}

div {
  margin-top: 5px;
}
</style>
