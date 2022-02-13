<template>
  <div id="app">
    <Main v-if="currentView == 'Main'" @startTest="setView('ReactionTest')"/>
    <ReactionTest v-else-if="currentView == 'ReactionTest'" @finishReactionTest="finishReactionHandler"/>
    <VisionTest v-else-if="currentView == 'VisionTest'" @finishVisionTest="finishVisionHandler"/>
    <Conclusion v-else-if = "currentView == 'Conclusion'"  @finishConclusion="finishConclusionHandler" :testResults ="testResults" />

  </div>
</template>

<script>
import Main from './components/Main.vue'
import ReactionTest from './components/ReactionTest.vue'
import VisionTest from './components/VisionTest.vue'
import Conclusion from './components/Conclusion.vue'

export default {
  name: 'App',
  components: {
    Main,
    ReactionTest,
    VisionTest,
    Conclusion
  },
  data() {
    return {
      currentView: 'Main',
      testResults: {
        reactions: [],
        visionResponses: 0,
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
      
      this.setView('VisionTest')
    },
    finishVisionHandler(results) {
        this.testResults.visuals = results
        console.log(this.testResults.visuals)
        this.setView('Conclusion')
    },
    finishConclusionHandler() {
      this.setView('Main')
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,400;0,500;0,700;0,800;0,900;1,400&display=swap');
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css";

#app {
  font-family: 'Rubik', Avenir, Helvetica, Arial, sans-serif !important;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin: 0;
  height: 100vh !important;
  max-width: 100vw;
  overflow-x: hidden;
  overflow-y: hidden;
  background: url(assets/bg.png);
  background-size: cover;
}
</style>
