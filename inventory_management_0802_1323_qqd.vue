// 代码生成时间: 2025-08-02 13:23:29
import { ref, reactive, onMounted } from 'vue';

// 响应式数据
const inventory = reactive([]);
const item = ref('');
const quantity = ref(0);

// 添加商品到库存
function addItem() {
  if (!item.value || quantity.value <= 0) {
    return;
  }
  const newItem = {
    id: inventory.length + 1,
    name: item.value,
    quantity: quantity.value,
  };
  inventory.push(newItem);
  item.value = '';
  quantity.value = 0;
}

// 从库存中删除商品
function removeItem(id) {
  inventory.splice(inventory.findIndex(item => item.id === id), 1);
}

// 生命周期钩子
onMounted(() => {
  console.log('组件已挂载');
  // 可以在这里加载初始库存数据
});
</script>

<style scoped>
/* 样式可以根据需要添加 */
</style>