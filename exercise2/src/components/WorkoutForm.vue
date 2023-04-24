
<template>
  <form @submit.prevent="submitForm">
    <div>
      <label for="workout-type">Type of Workout:</label>
      <select id="workout-type" v-model="workoutType">
        <option value="">Select a workout type</option>
        <option value="run">Run</option>
        <option value="weights">Weights</option>
      </select>
    </div>
    <div v-if="workoutType === 'run'">
      <label for="distance">Distance (in miles):</label>
      <input type="number" id="distance" v-model.number="distance">
      <label for="duration">Duration (in minutes):</label>
      <input type="number" id="duration" v-model.number="duration">
      <label for="calories">Calories Burned:</label>
      <input type="number" id="calories" v-model.number="calories">
    </div>
    <div v-if="workoutType === 'weights'">
      <label for="description">Description:</label>
      <input type="text" id="description" v-model.number="description" placeholder="ex: barbell bench">
      <label for="reps">Reps:</label>
      <input type="number" id="reps" v-model.number="reps">
      <label for="sets">Sets:</label>
      <input type="number" id="sets" v-model.number="sets">
      <label for="weight">Weight:</label>
      <input type="number" id="weight" v-model.number="weight">
    </div>
    <button type="submit" :disabled="!isValidForm">Add Workout</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      workoutType: '',
      distance: '',
      duration: '',
      calories: '',
      description: '',
      reps: '',
      sets: '',
      weight: ''
    }
  },
  computed: {
    isValidForm() {
      if (this.workoutType === 'run') {
        return this.distance && this.duration && this.calories;
      } else if (this.workoutType === 'weights') {
        return this.description && this.reps && this.sets && this.weight;
      } else {
        return false;
      }
    }
  },
  methods: {
    submitForm() {
      const workout = {
        type: this.workoutType,
        distance: this.distance,
        duration: this.duration,
        calories: this.calories,
        description: this.description,
        reps: this.reps,
        sets: this.sets,
        weight: this.weight
      };
      this.$emit('submit', workout);
      this.clearForm();
    },
    clearForm() {
      this.workoutType = '';
      this.distance = '';
      this.duration = '';
      this.calories = '';
      this.description = '';
      this.reps = '';
      this.sets = '';
      this.weight = '';
    }
  }
}
</script>
  <style scoped>
label{
    padding: 1rem;
    display: flex;
}
input{
    justify-content: end;
    margin-left: 1rem;
}
.workoutForm{
    display: block;
    width: 300px;
}
</style>
  