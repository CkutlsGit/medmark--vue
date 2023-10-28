<template>
    <div v-if="confirm" class="main">
        <section>
        <div class="header">
            <div class="header__content">
                <h2 class="header__logo">MedMark</h2>
                <h1>{{ login }}</h1>
            </div>
        </div>
        </section>
        <section class="intro">
            <div class="intro__content">
                <h1>How does it work?</h1>
                <p>
                    You need to specify 
                    the number of specific 
                    ratings in each input field.
                </p>
                <h3>Lets Go?</h3>
            </div>
        </section>
    </div>
    <div v-else>
        <login-input
            @confirmed="AcceptValuesfromLoginInput"
        >
        </login-input>
    </div>
</template>

<script>
import LoginInput from './LoginInput.vue';

export default {
    name: 'MedMark',
    components: {
        LoginInput
    },
    data() {
        return {
            login: '',
            confirm: false,
        }
    },
    methods: {
        AcceptValuesfromLoginInput(loginValue) {
            this.login = loginValue
            this.confirm = true
        }
    }
}
</script>

<style src="../../public/main.css" scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&family=Poppins:wght@400;600&display=swap');
</style>