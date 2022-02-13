<template>
  <div class="component-main">
    <div class="header">
      <h1>Drive Safer.</h1>
      <h4>Take our test to see if you're ready to hit the road.</h4>
    </div>
    <div class="svg-holder-car">
    </div>
    <button @click="$emit('startTest')" class="button is-primary fixed-bottom start-test">BEGIN TEST</button>
  </div>
</template>

<script>

export default {
  name: 'Main',
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

.component-main .header {
  padding: 40px;
  text-align: left;
  color: #FFFFFF;
}

.component-main .header h1 {
  font-size: 36px;
  font-weight: 800;
}

.component-main .header h4 {
  font-size: 24px;
  font-weight: 600;
}

.component-main .svg-holder-car {
  height: 400px;
  width: 105vw;
  margin: -50px auto;
  background-image: url(../assets/car.png);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.component-main .fixed-bottom {
  position: fixed;
  bottom: 50px;
  left: 50%;
  transform: translateX(-50%);
}

.component-main .start-test {
  color: black;
  background-color: rgb(253, 252, 239);
  width: 100px;
  font-size: 24px;
  width: 80%;

}

</style>
