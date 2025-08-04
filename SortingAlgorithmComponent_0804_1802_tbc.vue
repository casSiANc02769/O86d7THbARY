// 代码生成时间: 2025-08-04 18:02:22
import { ref, onMounted } from 'vue';

// 响应式数据
const array = ref([8, 4, 45, 6, 2, 1, 3]);
const sortedArray = ref([]);

// Bubble Sort
function bubbleSort() {
  const arr = [...array.value];
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        const temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  sortedArray.value = arr;
}

// Selection Sort
function selectionSort() {
  const arr = [...array.value];
  for (let i = 0; i < arr.length; i++) {
    let minIndex = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }
    const temp = arr[minIndex];
    arr[minIndex] = arr[i];
    arr[i] = temp;
  }
  sortedArray.value = arr;
}

// Insertion Sort
function insertionSort() {
  const arr = [...array.value];
  for (let i = 1; i < arr.length; i++) {
    let current = arr[i];
    let j = i - 1;
    while (j >= 0 && arr[j] > current) {
      arr[j + 1] = arr[j];
      j--;
    }
    arr[j + 1] = current;
  }
  sortedArray.value = arr;
}

// 生命週期钩子
onMounted(() => {
  console.log('Component is mounted, initial array:', array.value);
});

</script>

<style scoped>
/* 你可以在这里添加CSS样式 */
</style>
