// 代码生成时间: 2025-09-03 02:42:38
  <div class="interactive-chart-generator">
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import Chart from 'chart.js/auto'; // 请确保已安装chart.js

// 响应式数据
const chartCanvas = ref(null);
const chartInstance = ref(null);
const chartData = ref({
  labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
  datasets: [{
    label: '# of Votes',
    data: [12, 19, 3, 5, 2, 3],
    backgroundColor: [
      'rgba(255, 99, 132, 0.2)',
      'rgba(54, 162, 235, 0.2)',
      'rgba(255, 206, 86, 0.2)',
      'rgba(75, 192, 192, 0.2)',
      'rgba(153, 102, 255, 0.2)',
      'rgba(255, 159, 64, 0.2)'
    ],
    borderColor: [
      'rgba(255, 99, 132, 1)',
      'rgba(54, 162, 235, 1)',
      'rgba(255, 206, 86, 1)',
      'rgba(75, 192, 192, 1)',
      'rgba(153, 102, 255, 1)',
      'rgba(255, 159, 64, 1)'
    ],
    borderWidth: 1
  }]
});

// 生命周期钩子
onMounted(() => {
  createChart();
});

function createChart() {
  if (chartCanvas.value) {
    chartInstance.value = new Chart(chartCanvas.value, {
      type: 'bar',
      data: chartData.value,
      options: {
        scales: {
          y: {
            beginAtZero: true
          }
        }
      }
    });
  }
}
</script>

<style scoped>
.interactive-chart-generator {
  width: 100%;
  height: 400px;
}
</style>
