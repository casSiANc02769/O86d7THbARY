// 代码生成时间: 2025-10-04 02:29:20
import { ref, onMounted, reactive } from 'vue';

// 使用reactive使数据响应式
const patientRecord = reactive({
  name: '',
  age: 0,
  history: [],
  diagnosis: '',
  prescription: ''
});

// ref用来响应式地跟踪boolean值
const isLoading = ref(false);

// 生命周期钩子 onMounted
onMounted(async () => {
  isLoading.value = true;
  // 模拟加载电子病历数据
  setTimeout(() => {
    patientRecord.name = 'John Doe';
    patientRecord.age = 45;
    patientRecord.history = ['Hypertension', 'Diabetes'];
    patientRecord.diagnosis = 'Influenza';
    patientRecord.prescription = 'Tamiflu';
    isLoading.value = false;
  }, 1000);
});

</script>

<template>
  <div v-if="isLoading">
    Loading patient record...
  </div>
  <div v-else>
    <h1>Patient Record</h1>
    <p><strong>Name:</strong> {{ patientRecord.name }}</p>
    <p><strong>Age:</strong> {{ patientRecord.age }}</p>
    <ul>
      <li v-for="(item, index) in patientRecord.history" :key="index">Medical History: {{ item }}</li>
    </ul>
    <p><strong>Diagnosis:</strong> {{ patientRecord.diagnosis }}</p>
    <p><strong>Prescription:</strong> {{ patientRecord.prescription }}</p>
  </div>
</template>

<style scoped>
/* 你的样式代码 */
</style>