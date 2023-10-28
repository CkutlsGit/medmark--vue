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
            :disabled="login === ''"
        >
            Подтвердить
        </button>
        <button
            type="button"
            :disabled="login !== ''"
            @click="onConfirmAnonimus"
        >
            Остаться без логина
        </button>
    </section>
</template>

<script>
export default {
    name: 'LoginInput',
    data() {
        return {
            login: '',
        }
    },
    methods: {
        onConfirm() {
            this.$emit('confirmed',this.login)
        },
        onConfirmAnonimus() {
            const LoginAnonim = 'Anonim'
            this.$emit('confirmed', LoginAnonim)
        }
    }
}
</script>

<style>

</style>