// 代码生成时间: 2025-08-17 18:40:44
import { ref, onMounted } from 'vue';

// 原始数组
const array = ref([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]);
// 排序后的数组
const sortedArray = ref([]);

// 冒泡排序算法
function bubbleSort() {
    const length = array.value.length;
    for (let i = 0; i < length - 1; i++) {
        for (let j = 0; j < length - i - 1; j++) {
            if (array.value[j] > array.value[j + 1]) {
                // 交换元素
                let temp = array.value[j];
                array.value[j] = array.value[j + 1];
                array.value[j + 1] = temp;
            }
        }
    }
    sortedArray.value = [...array.value];
}

// 插入排序算法
function insertionSort() {
    for (let i = 1; i < array.value.length; i++) {
        let key = array.value[i];
        let j = i - 1;
        while (j >= 0 && array.value[j] > key) {
            array.value[j + 1] = array.value[j];
            j = j - 1;
        }
        array.value[j + 1] = key;
    }
    sortedArray.value = [...array.value];
}

// 生命周期钩子，组件挂载后输出初始数组
onMounted(() => {
    console.log('Initial array:', array.value);
});

</script>

<style scoped>
/* 你可以在这里添加一些CSS样式 */
</style>