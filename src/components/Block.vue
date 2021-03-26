<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Hit me</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0,
      }
    },
    // Lifestyle hooks
    // A hook to fire when the component is mounted
    mounted() {
      setTimeout(() => {
        this.showBlock = true
        this.startTimer()
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
        this.$emit('end', this.reactionTime)
      }
    }
}
</script>

<style>
.block {
    width: 500px;
    height: 500px;
    border-radius: 50px;
    background: rgb(12, 189, 150);
    color: #fff;
    text-align: center;
    padding: 20px 0;
    margin: 20px auto;
}
</style>