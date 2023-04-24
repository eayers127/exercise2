<template>
  <div>
    <workout-form @submit="addWorkout"></workout-form>
    <workout-table :workouts="workouts" @edit="editWorkout"></workout-table>
  </div>
</template>

<script>
import WorkoutForm from './components/WorkoutForm.vue';
import WorkoutTable from './components/WorkoutTable.vue';

export default {
  name: 'App',
  components: {
    WorkoutForm,
    WorkoutTable
  },
  data() {
    return {
      workouts: []
    }
  },
  methods: {
    addWorkout(workout) {
      this.workouts.push(workout);
    },
    editWorkout(index, workout) {
      this.workouts[index] = workout;
    }
  }
}
</script>

