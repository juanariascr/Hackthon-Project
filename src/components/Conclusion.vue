<template>
  <div class="component-conclusion">
      <pass v-if="result === 'pass'" />
      <avoid v-else-if="result === 'avoid'" />
      <fail v-else-if="result === 'fail'" />
      <button @click="$emit('finishConclusion')" class="button is-primary fixed-bottom start-test">Return Home</button>

  </div>
</template>


<script>
import Pass from './conclusions/Pass.vue'
import Avoid from './conclusions/Avoid.vue'
import Fail from './conclusions/Fail.vue'

export default {
  name: 'Conclusion',
  components: {
    Pass, Avoid, Fail
  },
  props: {
      testResults: {
        type: Object
      }
  },
  data() {
      return {
        result: '',
      }
  },
  methods: {
    calculateReactions() {
      let average = this.testResults.reactions.reduce((acc, prev) => acc + prev) / this.testResults.reactions.length
      return average < 450
    },

    calculateVisuals() {
      // Make sure they got all the answers right
      return this.testResults.visuals.reduce((acc, prev) => acc && prev, true)
    }
  },
  mounted() {
    let reactionsPass = this.calculateReactions() 
    let visualsPass = this.calculateVisuals()

    if(reactionsPass && visualsPass) {
      // Pass condition
      this.result = 'pass'
    } else if (reactionsPass || visualsPass) {
      // Avoid condition
      this.result = 'avoid'
    } else {
      // Fail condition
      this.result = 'fail'
    }
  }
}
</script>

<style>
.component-conclusion {
  width: 100vw;
  height: 100vh;
  background-size: cover;
}

.component-conclusion .fixed-bottom {
  position: fixed;
  bottom: 50px;
  left: 50%;
  transform: translateX(-50%);
}

.component-conclusion .start-test {
  color: black;
  background-color: rgb(253, 252, 239);
  width: 100px;
  font-size: 24px;
  width: 80%;

}
</style>
