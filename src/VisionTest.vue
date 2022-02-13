<template>
  <div class="component-vision-test">
      HELLO Vision Test!
      {{ actualAnswer }}
      <!--Stage-->
      <div id="stage"></div>
      <Letters size="12px" />
      <input type ="text" v-model="this.userAnswer" maxlength="5" />
      <button @click="handleClick">Submit</button>
  </div>
</template>

<script>
import Letters from './elements/Letters.vue'

export default {
  name: 'VisionTest',
  components: {
    Letters
    
  },
  props: {
  },
  data() {
      return {
        visionResponses: [],
        matchAnswer: false,
        userAnswer: 'text',
        actualAnswer: '',
      }
  },
  mounted() {
    // Add the Letters initially
    console.log('Adding Letters initially')
    this.addLetters()
  },
  methods: {
    
    handleClicked() {
        this.visionResponses.push(this.actualAnswer == this.userAnswer)
        
        // Go to next test
        if(this.visionResponses.length < 5) {
            this.addLetters()
        } else {
            this.$emit('finishVisionResponses', this.visionResponses)
        }
    },
    addLetters() {
        const letters = "zxcvbnmasdfghjklqwertyuiop"
        for(let i=0; i<5; i++)
        this.actualAnswer += letters[Math.floor(Math.random()*letters.length)]
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.component-reaction-test {
    color: red;
    font-size: 48px;
}
</style>