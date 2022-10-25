<template>
    <div>
        <p>Reaction time {{ score }} ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
</template>

<script setup>

</script>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score < 200) {
            this.rank = 'Gold Reaction Time'
        } else if (this.score < 400) {
            this.rank = 'Silver Reaction Time'
        } else {
            this.rank = 'Bronze Reaction Time'
        }
    }
}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: crimson;
    font-weight: bold;
}
</style>