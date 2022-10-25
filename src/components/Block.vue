<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
</template>

<script setup>

</script>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        // console.log('this component is mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            // console.log(this.showBlock)
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            // console.log(this.timer + 'timer')
            // console.log(this.reactionTime + 'reactiontime')
            this.$emit('endGame', this.reactionTime)
        }
    }
    // updated() {
    //     console.log('component updated')
    // },
    // unmounted() {

    // }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>