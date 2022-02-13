<template>
  <div class="component-conclusion component-avoid">
    <div class="header">
      <h1><span class="highlight-text">Avoid</span> the streets.</h1>
      <h4>You’re not fit to drive right now. Get a ride.</h4>
    </div>
    <div class="svg-holder">
    </div>
  </div>
</template>

<script>

export default {
  name: 'Avoid',
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
.component-avoid {
    background-image: url(../../assets/bg-avoid.png);
}

.component-conclusion .header {
  padding: 40px;
  text-align: left;
  color: #FFFFFF;
}

.component-conclusion.component-avoid .header {
    color: #413E21;
}

.component-conclusion .header h1 {
  font-size: 36px;
  font-weight: 800;
}

.component-conclusion .header h4 {
  font-size: 24px;
  font-weight: 600;
}

.component-avoid .highlight-text {
    background-color: #F2CB2D;
}

.component-conclusion .svg-holder {
  height: 400px;
  width: 105vw;
  margin: -50px auto;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.component-avoid .svg-holder {
    background-image: url(../../assets/avoid.png);
}

</style>
