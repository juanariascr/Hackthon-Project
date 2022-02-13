<template>
  <div class="component-reaction-test">
    <modal :active="showInstructions" primaryLabel="Start" title="Instructions" @click="hideInstructions" @cancel="hideInstructions">
        This test judges your reactions. Press the white dot when it appears.
    </modal>
    <div id="stage"></div>
    <Target :xPos="currentPos.x" :yPos="currentPos.y" v-if="showTarget" @click="handleClicked" />
  </div>
</template>

<script>
import Modal from './elements/Modal.vue'
import Target from './elements/Target.vue'

export default {
  name: 'ReactionTest',
  components: {
    Modal,
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
        },
        showInstructions: true,
      }
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
        this.currentPos.x = Math.floor((document.body.clientWidth  - 200) * Math.random() + 100) + 'px'
        this.currentPos.y = Math.floor((document.body.clientHeight - 200) * Math.random() + 100) + 'px'

        setTimeout(function() {
            this.showTarget = true
            this.startTime  = Date.now()
            console.log(this.currentPos)
        }.bind(this), Math.floor( 500 + (Math.random() * 1500)) )
    },
    hideInstructions() {
      this.showInstructions = false
      this.addTarget()
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
