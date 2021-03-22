<template>
    <button @click="inc">Increment</button>
    <button @click="dec">Decrement</button>
    <div>
        {{ counter }}
    </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    data() {
        return {
            counter: 0,
        };
    },
    computed: {
        doubleCounter(): number {
            return this.counter;
        },
    },
    watch: {
        counter(newVal, old) {
            console.log("counter is changed", newVal, old);
            if (newVal === 10) {
                alert("Stop!");
            }
        },
    },
    methods: {
        inc() {
            this.counter++;
        },
        dec() {
            this.counter--;
        },
    },
    created() {
        console.log("created");
    },
    mounted() {
        console.log("mounted");
    },
});
</script>
