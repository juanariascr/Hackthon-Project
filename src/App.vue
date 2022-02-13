<template>
  <div id="app">
    {{ currentView }}
    <Main v-if="currentView == 'home'" @startTest="setView('reactionTest')"/>
    <ReactionTest v-else-if="currentView == 'reactionTest'" @finishReactionTest="finishReactionHandler"/>
    <VisionTest v-else-if="currentView == 'visionTest'" @finishVisionTest="finishVisionHandler"/>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import ReactionTest from './components/ReactionTest.vue'
import VisionTest from './components/VisionTest.vue'

export default {
  name: 'App',
  components: {
    Main,
    ReactionTest,
    VisionTest
  },
  data() {
    return {
      currentView: 'home',
      testResults: {
        reactions: [],
        visionResponses: 0,
      },
      visualResults: {
        visuals: [],
      },
    }
  },
  methods: {
    setView(view) {
      this.currentView = view
    },
    finishReactionHandler(results) {
      this.testResults.reactions = results
      console.log(this.testResults.reactions)
      
      this.setView('visionTest')
    },
    finishVisionHandler(results) {
        this.visualResults.visuals = results
        console.log(this.visualResults.visuals)

        this.setView('Conclusion')
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,400;0,500;0,700;0,800;0,900;1,400&display=swap');
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css";

#app {
  font-family: 'Rubik', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin: 0;
  min-height: 100vh;
  overflow-x: hidden;
  overflow-y: hidden;
  background: url(assets/bg.png);
  background-size: cover;
}
</style>
