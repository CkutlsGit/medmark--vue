<template>
    <section class="login">
        <div class="login__content">
            <h1 class="login-ask">Can you write login?</h1>
        <input 
            type="text"
            v-model.trim="login"
            class="login-input"
        >
        <div class="login-buttons">
            <button
            type="button"
            @click="onConfirm"
            :disabled="login === ''"
            class="login-confirm"
        >
            Confirm login
        </button>
        <button
            type="button"
            :disabled="login !== ''"
            @click="onConfirmAnonimus"
            class="login-without"
        >
            Without login
        </button>
        </div>
        </div>
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

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&family=Poppins:wght@400;600&display=swap');
@import url('../../public/main.css');
</style>