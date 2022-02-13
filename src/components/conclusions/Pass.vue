<template>
  <div class="component-conclusion component-pass">
    <div class="header">
      <h1>Ready, set, <span class="highlight-text">go.</span></h1>
      <h4>You appear to be in good physical condition to get on the road. Drive safely!</h4>
    </div>
    <div class="svg-holder">
    </div>
  </div>
</template>

<script>

export default {
  name: 'Pass',
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

.component-pass .highlight-text {
    background-color: #152C1D;
}

.component-conclusion .svg-holder {
  height: 400px;
  width: 105vw;
  margin: -50px auto;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.component-pass .svg-holder {
    background-image: url(../../assets/pass.png);
}

</style>
