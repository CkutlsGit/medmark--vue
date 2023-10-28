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
            @click="confirm = true"
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
            confirm: false,
            login: ''
        }
    }
}
</script>

<style>

</style>