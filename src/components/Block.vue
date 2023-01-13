<template>
  <div class="block" v-if="showBlock" @click="stopTimer" ref="bl">
    Wciśnij
  </div>
</template>

<script>
export default {
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0
      }
    }, 

    props: ['delay'],

    mounted() {
      setTimeout(() =>{
        this.showBlock = true
        this.startTimer()
      }, this.delay)
    },

    methods: {
      startTimer() {
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10);
      },
      stopTimer() {
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
      }
    }
}
</script>

<style scoped>

.block{
    cursor: pointer;
    margin: 60px auto;
    width: 400px;
    padding: 100px 0;
    text-align: center;
    border-radius: 20px;
    background: #5283df;
    font-size: 24px;
    color: gold;
    box-shadow: inset 0 0 0 transparent, 2px 3px 40px 5px #000;
    transition: all 0.1s ease-in-out;
    text-transform: uppercase;
}
.block:active{
    text-shadow:  0 0 20px #000;
    box-shadow: inset 0 0 50px #444, 0 0 20px 0 #000;
}

</style>