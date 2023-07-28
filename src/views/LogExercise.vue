<template>
  <div id="app">
    <h1>Exercise Logging Form</h1>
    <form @submit.prevent="submitExercise">
      <div>
        <label for="exercise">Exercise Name:</label>
        <input type="text" id="exercise" v-model="exerciseName" required />
      </div>
      <div>
        <label for="duration">Duration (in minutes):</label>
        <input type="number" id="duration" v-model="duration" required />
      </div>
      <div>
        <label for="date">Date:</label>
        <input type="date" id="date" v-model="exerciseDate" required />
      </div>
      <button type="submit">Submit Exercise</button>
    </form>

    <div v-if="exerciseLog.length > 0">
      <h2>Exercise Log:</h2>
      <ul>
        <li v-for="(log, index) in exerciseLog" :key="index">
          {{ log.name }} - {{ log.duration }} minutes - {{ log.date }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

<script>
export default {
  data() {
    return {
      exerciseName: '',
      duration: '',
      exerciseDate: '',
      exerciseLog: []
    }
  },
  methods: {
    submitExercise() {
      if (this.exerciseName && this.duration && this.exerciseDate) {
        this.exerciseLog.push({
          name: this.exerciseName,
          duration: this.duration,
          date: this.exerciseDate
        })

        this.exerciseName = ''
        this.duration = ''
        this.exerciseDate = ''
      }
    }
  }
}
</script>
