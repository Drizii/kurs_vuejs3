<template>
    <div>
        <button @click="sayHello">Say Hello</button>
    </div>
</template>

<script>
export default {
  name: 'MyAwesomeComponent',
  setup() {
    function sayHello() {
    const welcomeText = 'Siema, co tam?'
        console.log(addExclamationMark(welcomeText));
        }
        function addExclamationMark(text) {
            return `${text}!`
        }
        return {sayHello}
  }
}
</script>

