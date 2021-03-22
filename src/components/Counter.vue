<template>
    <button :style="style" @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
    <div :style="otherStyle">
        {{ counter }}
    </div>
</template>
<script lang="ts">
import {
    computed,
    defineComponent,
    onMounted,
    reactive,
    ref,
    watch,
} from "vue";

export default defineComponent({
    setup() {
        // literal variables (number, boolean, string)
        const counter = ref(0);
        const doubleCounter = computed(() => counter.value);
        const increment = () => {
            logger();
            counter.value++;
        };

        const style = reactive({
            fontSize: "15px",
            color: "red",
        });
        /**
         * don't need to be returned coz it's not used for template
         */
        const logger = () => {
            console.log(counter.value);
        };
        const otherStyle = computed(() => {
            if (counter.value >= 10) {
                return {
                    color: "red",
                    fontSize: "20px",
                };
            } else {
                return {
                    color: "black",
                    fontSize: "10px",
                };
            }
        });
        console.log("created from composition");
        console.log(style.color);
        const decrement = () => {
            logger();
            counter.value--;
        };

        watch(counter, (newVal, old) => {
            console.log("counter is changed", newVal, old);
            if (newVal === 10) {
                alert("Stop!");
            }
        });

        onMounted(() => {
            console.log("mounted from composition");
        });
        return {
            counter,
            increment,
            decrement,
            doubleCounter,
            style,
            otherStyle,
        };
    },
});
</script>
