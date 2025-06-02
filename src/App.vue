<template>
    <h1>Reaction Timer</h1>
    <button type="button" @click="start" title="Play Game" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" />
</template>

<script>
// Global CSS
import "./components/css/global.css";

import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
    name: "App",
    data() {
        return {
            isPlaying: false,
            delay: null,
            score: null,
            showResults: false,
        };
    },
    components: { Block, Results },
    methods: {
        start() {
            this.delay = 2000 + Math.random() * 5000;
            this.isPlaying = true;
            this.showResults = false;
        },
        endGame(reactionTime) {
            this.score = reactionTime;
            this.isPlaying = false;
            this.showResults = true;
        },
    },
};
</script>

<style>
#app {
    height: 100dvh;
    align-content: center;
    color: #444;
    text-align: center;
    font-family: "Gill Sans MT", Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

button {
    width: 100px;
    height: 35px;
    cursor: pointer;
    font-family: inherit;
    margin: 0.5rem 0;
}

button[disabled] {
    cursor: default;
}
</style>
