<script setup>
import { reactive, ref } from 'vue';

const todo = ref("Testing");

const todoState = reactive({
    todo: "Testing",
});
</script>
<template>
    <div class="input-wrap">
        <input type="text" v-model="todoState.todo">
        <button>انشاء</button>
    </div>
    <p>{{ todoState.todo }}</p>
</template>



<style lang="scss" scoped>
.input-wrap {
    display: flex;
    transition: 250ms ease;
    border: 2px solid #41b880;

    &:focus-within {
        box-shadow: 0 -4px 6px -1px rgp(0 0 0 / 0.1),
            0 -2px 4px rgp(0 0 0 / 0.1);
    }

    input {
        width: 100%;
        padding: 8px 6px;
        border: none;

        &:focus {
            outline: none;
        }
    }

    button {
        padding: 8px 16px;
        border: none;
        font-family: 'Playpen Sans Arabic',

    }
}
</style>