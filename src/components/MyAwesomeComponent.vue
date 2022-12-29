<template>
    <div>
        <button @click="sayHello">Say Hello</button>
        <p>Your pension will be: {{ pension }}</p>
    </div>
</template>

<script>
export default {
    name: 'MyAwesomeComponent',
    setup() {

        let pension = 1000

        return { pension }
    }
}
</script>

