<template>
    <section class="login">
        <h1>Can you write login?</h1>
        {{ login }}
        <input 
            type="text"
            v-model.trim="login"
        >
        <button
            type="button"
            @click="onConfirm"
            :disabled="checkValidationLogin(correctLogin)"
        >
            Подтвердить
        </button>
    </section>
</template>

<script>
export default {
    name: 'LoginInput',
    data() {
        return {
            login: '',
            correctLogin: false
        }
    },
    methods: {
        onConfirm() {
            this.$emit('confirmed',this.login)
        },
        checkValidationLogin() {
            return this.login === ''
        }
    }
}
</script>

<style>

</style>