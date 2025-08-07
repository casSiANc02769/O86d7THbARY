// 代码生成时间: 2025-08-07 21:15:27
import { ref, onMounted } from 'vue';

// 创建响应式数据
const folders = ref([]);

// 添加文件夹
function addFolder() {
  const newFolderName = `Folder ${folders.value.length + 1}`;
  folders.value.push({ name: newFolderName });
}

// 重命名文件夹
function renameFolder(index) {
  const newFolderName = prompt(`Enter new name for folder at index ${index}:`);
  if (newFolderName) {
    folders.value[index].name = newFolderName;
  }
}

// 删除文件夹
function deleteFolder(index) {
  folders.value.splice(index, 1);
}

// 生命周期钩子 - 组件挂载后初始化文件夹列表
onMounted(() => {
  folders.value = [{ name: 'Folder 1' }, { name: 'Folder 2' }];
});
</script>
