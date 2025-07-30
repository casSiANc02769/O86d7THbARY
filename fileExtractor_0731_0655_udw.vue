// 代码生成时间: 2025-07-31 06:55:37
import { ref, onMounted, reactive } from 'vue';
import JSZip from 'jszip';
import { saveAs } from 'file-saver';

const state = reactive({
  file: null,
  error: null,
  message: null,
});

// 选择文件并处理文件数据
function handleFileChange(event) {
  const file = event.target.files[0];
  if (!file) return;

  state.file = file;
  state.error = null;
  state.message = '文件已选择，点击解压...';
}

// 解压文件
async function extractFile() {
  if (!state.file) {
    state.error = '请先选择一个文件';
    return;
  }

  try {
    const zip = new JSZip();
    const zipContent = await zip.loadAsync(state.file);
    const files = Object.keys(zipContent.files);
    const blobs = await Promise.all(files.map(async (file) => {
      return await zipContent.files[file].async('blob');
    }));

    const archive = new Blob(blobs, { type: 'application/zip' });
    saveAs(archive, 'extracted.zip');
    state.message = '文件解压成功';
  } catch (err) {
    state.error = '解压失败: ' + err.message;
  }
}

// 生命周期钩子
onMounted(() => {
  console.log('组件已挂载。');
});
</script>

<style scoped>
.error-message {
  color: red;
}

.info-message {
  color: green;
}
</style>

