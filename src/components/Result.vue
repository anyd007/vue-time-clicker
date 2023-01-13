<template>
  <p> twój wynik jest: {{ score /1000}} s</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>

export default {
    props: ['score'],

    data() {
        return {
            rank: null
        }
    },

    mounted() {
        if(this.score < 300){
            this.rank = 'jesteś jak NINJA'
        }
        else if(this.score < 500){
            this.rank = 'jesteś szybki ale postaraj się bardziej.....'
        }
        else if(this.score > 500){
            this.rank = 'możesz szybciej....'
        }
    }

}
</script>

<style>

</style>