<template>
    <div class="tasks" v-for="task in tasks" :key="task.id">
        <input type="checkbox" class="tasks__checkbox">
        <span>{{ task.name }}</span>
        <i class="fa-solid fa-trash tasks__icon" @click="handleEmit(task.id)"></i>
    </div>
</template>
<script>
export default {
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    methods: {
        handleEmit(id) {
            this.$emit("handleDeleteData", id)
        }
    }
}
</script>
<style lang="scss">
.tasks {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 10px 40px;
    border: 1px solid yellow;
    padding: 10px;
    border-radius: 10px;

    span {
        text-transform: uppercase;
        font-weight: 550;
        font-size: 12px;
    }

    .tasks__icon {
        cursor: pointer;
    }
}
</style>