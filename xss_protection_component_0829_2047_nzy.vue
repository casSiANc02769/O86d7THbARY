// 代码生成时间: 2025-08-29 20:47:41
import { defineComponent, ref, onMounted } from 'vue';
import DOMPurify from 'dompurify';

export default defineComponent({
  name: 'XssProtectionComponent',

  setup() {
    // Response data
    const htmlContent = ref('');
    const safeHtmlContent = ref('');

    // Fetch data and sanitize using lifecycle hooks
    onMounted(() => {
      fetchHtmlContent();
    });

    function fetchHtmlContent() {
      // Simulate fetching HTML content that might be unsafe
      htmlContent.value = "<script>alert('XSS')</script>";
      // Sanitize the HTML content
      safeHtmlContent.value = DOMPurify.sanitize(htmlContent.value);
    }

    return {
      htmlContent,
      safeHtmlContent
    };
  }
});
</script>
