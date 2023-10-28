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
            Confirm login
        </button>
        <button
            type="button"
            :disabled="login !== ''"
            @click="onConfirmAnonimus"
        >
            Log in without a login
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

<style >
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&family=Poppins:wght@400;600&display=swap');
</style>