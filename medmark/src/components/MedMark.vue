<template>
    <div v-if="confirm" class="main">
        <header>
        <div class="header">
            <div class="header__content">
                <h2 class="header__logo">MedMark</h2>
                <h1 class="header__login">{{ login }}</h1>
            </div>
        </div>
        </header>
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
        <section class="inputs">
            <div class="input__form">
                <div class="input__block">
                    <label>5</label>
                    <input 
                    type="number" class="input-five" min="0"
                    v-model="fiveMark"
                    >
                </div>
                <div class="input__block">
                    <label>4</label>
                    <input 
                    type="number" class="input-four" min="0"
                    v-model="fourMark"
                    >
                </div>
                <div class="input__block">
                    <label>3</label>
                    <input 
                    type="number" class="input-three" min="0"
                    v-model="threeMark"
                    >
                </div>
                <div class="input__block">
                    <label>2</label>
                    <input 
                    type="number" class="input-two" min="0"
                    v-model="twoMark"
                    >
                </div>
            </div>
        </section>
        <section class="endmark">
            <div class="endmark__content">
                <h1 v-if="isNaN(FindendMark)">Final mark:  Enter your marks</h1>
                <h1 v-else>Final mark: {{ FindendMark.toFixed(2) }}</h1>
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
            fiveMark: 0,
            fourMark: 0,
            threeMark: 0,
            twoMark: 0,
        }
    },
    computed: {
        FindendMark() {
            return (this.fiveMark * 5 + this.fourMark * 4 + this.threeMark * 3 + this.twoMark * 2) / (this.fiveMark + this.fourMark + this.threeMark + this.twoMark)
        }
    },
    watch: {
        fiveMark(newValue) {
            this.validateAndSet(newValue, 'fiveMark')
        },
        fourMark(newValue) {
            this.validateAndSet(newValue, 'fourMark')
        },
        threeMark(newValue) {
            this.validateAndSet(newValue, 'threeMark')
        },
        twoMark(newValue) {
            this.validateAndSet(newValue, 'twoMark')
        },
    },
    methods: {
        AcceptValuesfromLoginInput(loginValue) {
            this.login = loginValue
            this.confirm = true
        },
        validateAndSet(newValue, propName) {
            if (newValue < 0 || newValue === '') {
                this[propName] = 0
            }
        }
    }
}
</script>

<style src="../../public/main.css" scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&family=Poppins:wght@400;600&display=swap');
</style>