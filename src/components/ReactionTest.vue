<template>
  <div class="component-reaction-test">
      <div id="stage"></div>
      <Target :xPos="currentPos.x" :yPos="currentPos.y" v-if="showTarget" @click="handleClicked" />
  </div>
</template>

<script>
import Target from './elements/Target.vue'

export default {
  name: 'ReactionTest',
  components: {
    Target
  },
  props: {
    msg: String
  },
  data() {
      return {
        reactionTimes: [],
        showTarget: false,
        startTime: -1,
        currentPos: {
            x: '0px',
            y: '0px'
        }
      }
  },
  mounted() {
    // Add the target initially
    console.log('Adding target initially')
    this.addTarget()
  },
  methods: {
    handleClicked() {
        this.reactionTimes.push(Date.now() - this.startTime)
        this.showTarget = false

        // Go to next test
        if(this.reactionTimes.length < 5) {
            this.addTarget()
        } else {
            this.$emit('finishReactionTest', this.reactionTimes)
        }
    },

    addTarget() {
        setTimeout(function() {
            this.showTarget = true
            this.startTime  = Date.now()
            this.currentPos.x = Math.floor((document.body.clientWidth  - 100) * Math.random() + 100) + 'px'
            this.currentPos.y = Math.floor((document.body.clientHeight - 100) * Math.random() + 100) + 'px'
            console.log(this.currentPos)
        }.bind(this), Math.floor( 500 + (Math.random() * 1500)) )
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
