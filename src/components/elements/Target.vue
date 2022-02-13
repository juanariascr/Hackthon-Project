<template>
    <div :style="{ top: yPos, left: xPos }" class="reaction-target"></div>
</template>

<style>
.reaction-target {
    height: 100px;
    width: 100px;
    top: 50%;
    left: 50%;
    position: absolute;
    background-color: white;
    border-radius: 100%;
}
</style>

<script>
export default {
    name: 'Target',
    props: {
        xPos: String,
        yPos: String,
    },
    methods: {
        printPositions() {
            console.log(this.xPos, this.yPos)
        }
    },
}
</script>