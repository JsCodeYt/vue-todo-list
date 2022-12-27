<template>
    <header class="header">
        <form class="header__form" @submit.prevent>
            <input type="text" @input="name = $event.target.value">
            <button class="header__btn btn btn-outline-success" @click="handleSend(name)">Join</button>
            <button class="header__btn btn btn-outline-danger" @click="handleClear">Clear</button>
        </form>
    </header>
</template>
<script>

export default {
    data() {
        return {
            name: "",
        }
    },
    methods: {
        handleSend(item) {
            this.$emit("handleData", item)
        },
        handleClear() {
            localStorage.clear()
            window.location.replace("/")
        }
    }
}
</script>
<style lang="scss">
.header {
    padding: 10px;
    margin: 20px 0px;
    border-bottom: 3px solid #232323;
    position: sticky;
    top: 0;
    background-color: white;
    z-index: 999;

    .header__form {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1rem;

        input {
            height: 34px;
            width: 300px;
            border-radius: 5px;
            outline: none;
            border: 3px solid #bde0fe;
            padding: 0px 10px;
            font-size: 17px;
        }

        button {
            padding: 2px 20px;
            border-radius: 4px;
            outline: none;
        }
    }
}
</style>