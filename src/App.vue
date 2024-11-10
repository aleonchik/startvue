<template>
    <h3>{{ info }}</h3>
    <p>{{ someInfo }}</p>

    <!-- Если параметр в userData() не передан будет подставлен по умолчанию -->
    <button type="button" @click="userData('Передали параметр')">Отправить</button>
    <!-- <button type="button" :click="">Отправить</button> -->
    <!-- <button type="button" v-on:click="">Отправить</button> -->

</template>


<script>
    export default {
        data() {
            return {
                info: 'Tiiitle!',
                someInfo: 'Anonse of message!'
            }
        },

        methods: {
            userData(word = 'Параметр по умолчания') {
                // this.info = 'Some new VALUE'
                // this.someInfo = 'Values for someInfo'
                this.someInfo = word
            }
        }
    }
</script>


<style scoped>
    h3 {
        font-weight: lighter;
    }

    p {
        color: rgb(203, 31, 31)
    }
</style>
