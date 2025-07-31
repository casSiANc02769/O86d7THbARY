// 代码生成时间: 2025-07-31 12:34:11
import { ref, onMounted, onUnmounted } from 'vue';

export default {
  name: 'ResponsiveLayoutComponent',
  data() {
    return {
      isSmallScreen: false,
    };
  },
  setup() {
    const isSmallScreen = ref(false);
    
    const checkScreenSize = () => {
      isSmallScreen.value = window.innerWidth < 768;
    };
    
    onMounted(() => {
      checkScreenSize();
      window.addEventListener('resize', checkScreenSize);
    });
    
    onUnmounted(() => {
      window.removeEventListener('resize', checkScreenSize);
    });
    
    return {
      isSmallScreen
    };
  }
};
</script>

<style scoped>
.container {
  padding: 20px;
}

.is-small {
  background-color: lightblue;
}

@media (max-width: 768px) {
  .container {
    background-color: lightgreen;
  }
}
</style>