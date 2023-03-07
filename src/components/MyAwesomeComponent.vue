<template>
    <div>
        <div>
            <p>Masks: {{masks}}</p>
            <p v-if="masks > 3">You can buy mask</p>
            <p v-else-if="masks > 0 && masks <= 3">You can buy a mask, but hurry up!</p>
            <p v-else>You can't buy a mask, it's out of stock!</p>
            <button
                class="btn"
                @click="buyMask"
                :disabled="!masks"
                :class="{'btn--warning': masks > 0 && masks <= 3 }"
                >
                Buy a mask
            </button>
        </div>
        <div>
            <img :src="images[currentImage]" :alt="'Image ${currentImage + 1}'" class="image"/>
            <button
            class="btn"
            @click="changeImage"
            :disabled="currentImage >= images.length - 1"
            >
            Change Image
            </button>
        </div>
    </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";

export default {
    name: 'MyAwesomeComponent',
    setup() {
        const masks = ref(5);

        const styles = reactive({
            btn: {
            backgroundColor: '#17a2b8',
            color: '#fff',
            }
        });

        function buyMask(){
            masks.value--;
        }

        const images = ref([
            'https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Bruce_McCandless_II_during_EVA_in_1984.jpg/800px-Bruce_McCandless_II_during_EVA_in_1984.jpg',
            'https://static.prsa.pl/images/bbf914a4-ec68-4b8b-a149-b793c8916f49.file?format=700',
            'https://img.freepik.com/darmowe-wektory/astronauta-trzymajac-gwiazda-kreskowka-wektor-ikona-ilustracja-technologia-kosmiczna-ikona-koncepcja-bialym-tle-premium-wektor-plaski-styl-kreskowki_138676-3495.jpg?w=2000',
            'https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/Ed_White_performs_first_U.S._spacewalk_crop.jpg/1200px-Ed_White_performs_first_U.S._spacewalk_crop.jpg',
            'https://www.decormint.com/storage/thumbs/fotolia/132366202/thumbnw_d5f15aeea722b89a1447de5f19c6e095.jpg',
        ]);

        const currentImage = ref(0);

        function changeImage() {
            currentImage.value++
            }

        return {masks, buyMask, ...toRefs(styles), images, currentImage, changeImage}
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
    &--warning {
        background-color: #ffc107;
        color: #000;
    }
    &:disabled {
        cursor: default;
        background-color: #bd2130;
    }
}
.image {
    margin-top: 200px;
    width: 200px;
    display: block;
}

</style>
