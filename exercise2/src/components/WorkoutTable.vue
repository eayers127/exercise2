
  
  <template>
    <table>
      <thead>
        <tr>
          <th>Type</th>
          <th v-if="showDistance">Distance (miles)</th>
          <th v-if="showDuration">Duration (min)</th>
          <th v-if="showCalories">Calories Burned</th>
          <th v-if="showDescription">Description</th>
          <th v-if="showReps">Reps</th>
          <th v-if="showSets">Sets</th>
          <th v-if="showWeight">Weight (lbs)</th>
          <th>Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(workout, index) in workouts" :key="index">
          <td>{{ workout.type }}</td>
          <td v-if="showDistance">{{ workout.distance }}</td>
          <td v-if="showDuration">{{ workout.duration }}</td>
          <td v-if="showCalories">{{ workout.calories }}</td>
          <td v-if="showDescription">{{ workout.description }}</td>
          <td v-if="showReps">{{ workout.reps }}</td>
          <td v-if="showSets">{{ workout.sets }}</td>
          <td v-if="showWeight">{{ workout.weight }}</td>
          <td><button @click="deleteWorkout(index)">Delete</button></td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script>
  export default {
    props: {
      workouts: {
        type: Array,
        required: true
      }
    },
    data() {
      return {
        editedWorkoutIndex: null
      }
    },
    computed: {
      showDistance() {
        return this.workouts.some(w => w.type === 'run');
      },
      showDuration() {
        return this.workouts.some(w => w.type === 'run');
      },
      showCalories() {
        return this.workouts.some(w => w.type === 'run');
      },
      showDescription() {
        return this.workouts.some(w => w.type === 'weights');
      },
      showReps() {
        return this.workouts.some(w => w.type === 'weights');
      },
      showSets() {
        return this.workouts.some(w => w.type === 'weights');
      },
      showWeight() {
        return this.workouts.some(w => w.type === 'weights');
      }
    },
    methods: {
      deleteWorkout(index) {
        this.$emit('delete', index);
      }
    }
  }
  </script>

  
  <style scoped>
  table, th, td {
  border: 1px solid;
  border-collapse: collapse;
  padding: 1rem;
  text-align: center;
}
tr:hover {background-color: coral;}

</style>
  