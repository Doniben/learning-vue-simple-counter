<template>
  <h2>{{ title }}</h2>
  <p>{{ counter }}<sup>{{ currentPower }}</sup> = {{ squareResult }}</p>

  <button @click="increment">+1</button>
  <button @click="decrement">-1</button>

</template>

<script>
export default {
    props: {
        title: {
            type: String,
            default: 'Counter',
        },
        start: {
            type: Number,
        },
        power: {
            type: Number,
            default: null
        }
    },
    data() {
        return {
            counter: this.start,
        }
    },
    watch: {
        start(newVal) {
            this.counter = newVal;
        },
        counter(newVal) {
            this.$emit('update-input-value', newVal)
        }
    },
    methods: {
        increment() {
            this.counter++;
        },
        decrement() {
            this.counter--;
        }
    },
    computed: {
        currentPower() {
            return this.power !== null ? this.power : this.counter;
        },
        squareResult() {
            return Math.pow(this.counter, this.currentPower);
        }
    }
}
</script>

<style>
button {
    margin: 0.5rem;
    padding: 0.5rem 1rem;
    background-color: #64B687;
    border-radius: 5px;
    border: solid 1px grey;
}

button:hover {
    background-color: #5aa67b;
    cursor: pointer;
}

</style>