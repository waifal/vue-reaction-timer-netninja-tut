<template>
    <div class="block" v-if="showBlock" @click="stopTimer"><small>Click Me</small></div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        };
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit("end", this.reactionTime);
        },
    },
};
</script>

<style>
.block {
    cursor: pointer;
    width: 400px;
    margin: 40px auto;
    padding: 100px 0;
    color: #fff;
    text-align: center;
    border-radius: 20px;
    background: #0faf87;
    transition: box-shadow 0.2s linear;
}

.block:hover {
    box-shadow: 0 0 12px 0 rgb(0 0 0 / 10%);
}
</style>
