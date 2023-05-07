<template>
    <div class="results">
        <p style="font-size: 20px;">Reaction Time: {{ score }} ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
</template>

<script>
export default {
    name: 'Results',
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score <= 250) {
            this.rank = 'Fast and furious eh ?';
        }
        else if (this.score < 400) {
            this.rank = 'Hmmm.... Good reflexes'
        }
        else {
            this.rank = 'Ha ha ha..... Slow Poke !'
        }
    },
}
</script>

<style>
.rank {
    font-size: 35px;
    color: green;
    font-weight: bold;
}

.results {
    text-align: center;
}
</style>