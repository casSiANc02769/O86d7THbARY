// 代码生成时间: 2025-08-01 14:42:30
import { ref, onMounted } from 'vue';
import axios from 'axios';

// 响应式数据
const posts = ref([]);

// 获取帖子的函数
const fetchPosts = async () => {
  try {
    const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
    posts.value = response.data;
  } catch (error) {
    console.error('Failed to fetch posts:', error);
  }
};

// 生命周期钩子
onMounted(fetchPosts);
</script>

<style scoped>
/* 这里可以添加CSS样式 */
</style>