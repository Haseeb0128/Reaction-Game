<template>
    <div class="box" v-if="showBox" @click="stopTimer">Hurry up and Click me !</div>
</template>

<script>
export default {
    name: 'Block',
    data() {
        return {
            showBox: false,
            timer: null,
            reactionTime: 0,
        }
    },
    props: ['delay'],
    mounted() {
        // This function runs after the delay time.
        setTimeout(() => {
            // Displays the box after the delay time
            this.showBox = true;
            // Starts to calculate the reaction time as the component is mounted to the DOM
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            // Calculates the reaction time
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            // Clears the interval to stop the calculation of reaction time
            clearInterval(this.timer);
            // Custom event so that reaction time is accessible to the parent component
            this.$emit('end', this.reactionTime);
        }
    }
}
</script>

<style>
.box {
    margin: 25px;
    width: 500px;
    height: 300px;
    background-color: green;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 30px;
    color: white;
    cursor: pointer;
    border-radius: 30px;
}
</style>