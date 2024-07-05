<template>
  <div id="app">
    <header>
      <h1>成绩录入</h1>
    </header>
    <main>
      <div class="score-input">
        <label for="student-name">学生姓名:</label>
        <input type="text" id="student-name" name="student-name" required>
        <label for="course">选择课程:</label>
<select id="course" name="course" required>
  <option value="">请选择</option>
  <option value="course1">语文</option>
  <option value="course2">数学</option>
  <option value="course3">英语</option>
  <option value="course4">政治</option>
  <option value="course5">生物</option>
  <option value="course6">地理</option>
  <option value="course7">历史</option>
  <option value="course8">物理</option>
  <option value="course9">化学</option>
</select>
      </div>
      <div class="score-input">
        <label for="classwork">平时分:(50%)</label>
        <input type="number" id="classwork" v-model.number="classworkScore" />
      </div>
      <div class="score-input">
        <label for="finalExam">期末成绩:(50%)</label>
        <input type="number" id="finalExam" v-model.number="finalExamScore" />
      </div>
      <div class="score-input">
        <label for="totalScore">总成绩:</label>
        <input type="number" id="totalScore" :value="totalScore" readonly />
      </div>
      <button @click="calculateTotalScore">录入成绩</button>
      <div v-if="showSuccessAlert" class="alert">
      <p>录入成功!</p>
      <button @click="showSuccessAlert = false">关闭</button>
    </div>
    </main>
    <footer>
      <p>© 2024 成绩录入系统</p>
    </footer>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'App',
  setup() {
    const courseName = ref('')
    const classworkScore = ref(0)
    const finalExamScore = ref(0)
    const totalScore = computed(() => {
      return (classworkScore.value * 0.5) + (finalExamScore.value * 0.5)
    })

    const calculateTotalScore = () => {
      // 在这里可以添加其他业务逻辑,如保存成绩等
      console.log(`总成绩: ${totalScore.value}`)
    }

    return {
      courseName,
      classworkScore,
      finalExamScore,
      totalScore,
      calculateTotalScore
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

header, main, footer {
  padding: 20px;
}

.score-input {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.score-input label {
  margin-right: 10px;
}

.score-input input {
  width: 200px;
  padding: 5px;
  font-size: 16px;
}

button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}
</style>
