<template>
    <div class="block" v-if="showBlock" @click.right="hideblock" @click.left="stopTimer">
        <p>click me</p>
        <h3 v-if="showScore">score: {{ yourScore }}</h3>
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTimer: 0,
            showScore: false,
            yourScore: 0
        }
    },
    methods: {
        hideblock(){
            this.showBlock = false
            this.$emit('closeBlock')
        },
        startTimer() {
            this.timer = setInterval(
                () => { this.reactionTimer += 100 },
                100
            )
        },
        stopTimer() {
            clearInterval(this.timer)
            this.showScore = true
            this.yourScore = this.reactionTimer
        },
    },
    created() {
        console.log('created')
    },
    mounted() {
        console.log('mounted '+this.delay)
        setTimeout(
            () => {
                this.showBlock = true
                this.startTimer()
            },
            this.delay
        )
    },
    updated() {
        console.log('updated')
    },
    unmounted() {
        console.log('unmounted')
    },
}
</script>

<style scoped>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #67db67;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: auto;
    }
</style>