<template>
  <div class="component-vision-test">
      <modal :active="showInstructions" primaryLabel="Start" title="Instructions" @click="hideInstructions" @cancel="hideInstructions">
        This test judges your vision. Read the text and enter what you see. Remove any corrective lenses. Hold your device at an arm's length away. Do not zoom into the text.
      </modal>
      <!--Stage-->
      <div id="stage">
        <span class="vision-test">{{ actualAnswer }}</span>
        <input v-on:keyup.enter="handleClicked" class="input is-primary" placeholder="Enter your response" type ="text" v-model="this.userAnswer" maxlength="5" />
        <br>
        <button class="button large is-primary" @click="handleClicked">Submit</button>
      </div>
  </div>
</template>

<script>
import Modal from './elements/Modal.vue'

export default {
  name: 'VisionTest',
  components: {
    Modal
  },
  props: {
  },
  data() {
      return {
        visionResponses: [],
        matchAnswer: false,
        userAnswer: '',
        actualAnswer: '',
        showInstructions: true,
      }
  },
  methods: {
    handleClicked() {
      console.log(this.visionResponses)
      this.visionResponses.push(this.actualAnswer === this.userAnswer.toLowerCase())

      // Go to next test
      if(this.visionResponses.length < 5) {
          this.addLetters()
      } else {
          this.$emit('finishVisionTest', this.visionResponses)
      }
    },

    addLetters() {
        const letters = "zxcvbnmasdfghjklqwertyuiop"
        this.actualAnswer = ''
        this.userAnswer = ''
        for(let i=0; i<5; i++)
          this.actualAnswer += letters[Math.floor(Math.random() * letters.length)]
    },

    hideInstructions() {
      this.showInstructions = false
      this.addLetters()
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

.component-vision-test {
    height: 100%;
    width: 100%;
    background-color: white;
}

.component-vision-test #stage {
  text-align: center;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  min-width: 80vw;
  left: 50%;

}

.component-vision-test .vision-test {
  color: black;
  text-transform: uppercase;
  font-size: 10px;
  margin: 10px;
}
</style>
