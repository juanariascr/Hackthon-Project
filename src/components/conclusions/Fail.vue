<template>
  <div class="component-conclusion component-fail">
    <div class="header">
      <h1>Be <span class="highlight-text">safe.</span> Get a ride.</h1>
      <h4>You’re not fit to drive right now. Don't be risk to yourself and others.</h4>
    </div>
    <div class="svg-holder">
    </div>
  </div>
</template>

<script>

export default {
  name: 'Fail',
  components: {
  },
  props: {
    
  },
  data() {
    return {
      textString: 'text',
      showInstructions: true,
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.component-fail {
    background-image: url(../../assets/bg-fail.png);
}

.component-conclusion .header {
  padding: 40px;
  text-align: left;
  color: #FFFFFF;
}

.component-conclusion .header h1 {
  font-size: 36px;
  font-weight: 800;
}

.component-conclusion .header h4 {
  font-size: 24px;
  font-weight: 600;
}

.component-fail .highlight-text {
    background-color: #8C1E0F;
}

.component-conclusion .svg-holder {
  height: 400px;
  width: 105vw;
  margin: -50px auto;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.component-fail .svg-holder {
    background-image: url(../../assets/fail.png);
}

</style>
