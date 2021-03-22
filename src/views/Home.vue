<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <Counter />
        <Counter2 />
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Counter from "@/components/Counter.vue"; // @ is an alias to /src
import Counter2 from "@/components/Counter2.vue"; // @ is an alias to /src

export default defineComponent({
    name: "Home",
    components: {
        Counter,
        Counter2,
    },
});
</script>
