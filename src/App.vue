<template>
  <div id="app">
    {{ currentView }}
    <Main v-if="currentView == 'home'" @startTest="setView('reactionTest')"/>
    <ReactionTest v-else-if="currentView == 'reactionTest'" @finishReactionTest="finishReactionTest"/>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import ReactionTest from './components/ReactionTest.vue'

export default {
  name: 'App',
  components: {
    Main,
    ReactionTest,
  },
  data() {
    return {
      currentView: 'home',
      testResults: {
        reactions: [],
      },
    }
  },
  methods: {
    setView(view) {
      this.currentView = view
    },
    finishReactionTest(results) {
      this.testResults.reactions = results
      console.log(this.testResults.reactions)
      
      this.setView('visionTest')
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,400;0,500;0,700;0,800;0,900;1,400&display=swap');

#app {
  font-family: 'Rubik', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  min-height: 100vh;
  overflow-x: hidden;
  overflow-y: hidden;
  background: url(assets/bg.png);
  background-size: cover;
}
</style>
