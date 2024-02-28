<template>
    <div class="result">
        <p>Reaction time - {{ score }} ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
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
        if (this.score < 200) {
            this.rank = "Ninja"
        } else if (this.score < 300) {
            this.rank = "Samurai"
        } else if (this.score < 400) {
            this.rank = "Warrior"
        } else if (this.score < 500) {
            this.rank = "Average Joe"
        } else {
            this.rank = "Snail"
        }
    }
}
</script>

<style >
.rank {
    font-size: 24px;
    color: #0faf87;
}
</style>