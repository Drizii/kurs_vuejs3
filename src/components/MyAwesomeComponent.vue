<template>
    <div>
        <p>Masks: {{masks}}</p>
        <p v-if="masks > 3">You can buy mask</p>
        <p v-else-if="masks > 0 && masks <= 3">You can buy a mask, but hurry up!</p>
        <p v-else>You can't buy a mask, it's out of stock!</p>
        <button
            class="btn"
            @click="buyMask"
            :disabled="!masks"
            :style="{backgroundColor: '#007bff', color: '#000'}"
            >
            Buy a mask
        </button>
    </div>
</template>

<script>
import { ref } from "vue";

export default {
    name: 'MyAwesomeComponent',
    setup() {
        const masks = ref(5);
        function buyMask(){
            masks.value--;
        }

        return {masks, buyMask}
    }
};
</script>

<style lang="scss">
.btn {
    color: #fff;
    background-color: #369b6d;
    border: none;
    padding: 5px 10px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.1 ease-in;
    &:disabled {
        cursor: default;
        background-color: #bd2130;
        }
}

</style>
