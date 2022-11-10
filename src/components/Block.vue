<template>
  <div class = "block" v-if ="showBlock" @click="stopTimer">
    Click Here
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return {
            showBlock:false,
            timer:null,
            reactiontime:0
        }
    },

    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },

    methods:{
        startTimer(){
            this.timer = setInterval(() =>{
                this.reactiontime += 10
            },10)

        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactiontime)
        },
    }

}
</script>

<style>

.block{
    width: 500px;
    border-radius: 20px;
    background: cyan;
    color:black;
    text-align: center;
    padding: 100px 0;
    margin:40px auto;
}

</style>