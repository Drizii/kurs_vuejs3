<template>
    <div>
        <button @click="incrementPension">Increment My Pension</button>
        <p>Your pension will be: {{ pension }}</p>
    </div>
</template>

<script>
import { ref } from "vue";

export default {
    name: 'MyAwesomeComponent',
    setup() {
        let pension = ref(100);

        function incrementPension() {
            pension.value++;
        }

        return { pension, incrementPension };
    }
}
</script>

