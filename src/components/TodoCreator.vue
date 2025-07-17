<script setup>
import { defineEmits, reactive, ref } from 'vue';
import TodoButton from './TodoButton.vue';

const emit = defineEmits(["create-todo"]);
const todoState = reactive({
    todo: "",
    invalid: null,
    errMsg: "",
});
const createTodo = () => {
    todoState.invalid = null;
    if (todoState.todo !== "") {
        emit("create-todo", todoState.todo);
        todoState.todo = "";
        return;
    }
    todoState.invalid = true;
    todoState.errMsg = "لايمكن ان تكون المهمة فارغة";
};

</script>
<template>
    <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
        <input type="text" v-model="todoState.todo">
        <TodoButton @click="createTodo()" />
    </div>
    <p class="err-msg" v-show="todoState.invalid"> {{ todoState.errMsg }}</p>
</template>



<style lang="scss" scoped>
.input-wrap {
    display: flex;
    transition: 250ms ease;
    border: 2px solid #41b880;

    &.input-err {
        border-color: red;
    }

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

}

.err-msg {
    margin-top: 6px;
    font-size: 12px;
    text-align: center;
    color: red;


}
</style>