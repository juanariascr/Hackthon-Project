<template>
  <div class="component-conclusion">
      HELLO2.0!
      <br>
      <button class="button large is-primary" @click="CalculateValues">Calculate Avg Reaction Score</button>
      <br>
      {{Avg}}{{" : "}}{{temp}}
      <br>
      <br>
      <button class="button large is-primary" @click="CalculateVision">Calculate Vision Score</button>
      <br>
      {{vision}}{{" : "}}{{visiontemp}}
      <!--Stage-->
  </div>
</template>


<script>

export default {
  name: 'Conclusion',
  components: {
  },
  props: {
      testResults: {
        type: Object
      }
  },
  data() {
      return {
        Avg: 0,
        temp: '',
        vision: 0,
        visiontemp: ''
      }
  },
  methods: {
    CalculateValues() {
      this.Avg = (this.testResults.reactions[0]+this.testResults.reactions[1]+this.testResults.reactions[2]+this.testResults.reactions[3]+this.testResults.reactions[4])/5
      if(this.Avg > 450){
        this.temp = 'fail'
      }
      else{
        this.temp = 'pass'
      }
    },

    CalculateVision() {
      for(let i=0; i<5; i++){
        this.vision += this.testResults.visuals[i]
      }
      if(this.vision >= 4){
        this.visiontemp = 'pass'
      }
      else{
        this.visiontemp = 'fail'
      }
    }
  }
}
</script>

<style>
.component-conclusion {
    color: red;
    font-size: 48px;
}
</style>
