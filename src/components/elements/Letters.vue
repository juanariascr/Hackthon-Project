<template>
  <div :style="{ fontSize: size } " class="vision-letters"></div>
</template>

<style>
.vision-letters {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  position: absolute;
  background-color: white;
  border-radius: 100%;
}
</style>

<script>
export default {
  name: "Letters",
  props: {
      size: String
  },
  methods: {},
};
</script>
