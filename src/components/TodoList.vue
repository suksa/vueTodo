<template>
    <div>
        <transition-group name="list" tag="ul" >
            <li v-for="(todo,index) in todos" :key="todo.id">
                <button
                    :class="{check:todo.compleate}"
                    @click="ck(index)">CHECK
                </button>
                {{todo.data}}
                <button @click="TodoDel(index)">삭제</button>
            </li>
        </transition-group>
    </div>
</template>

<script>
    export default {
        props:['todos'],
        methods:{
            ck(index){
                this.$emit('ckToggle',index)
            },
            TodoDel(index){
                this.$emit('TodoDel',index)
            }
        }
    }
</script>

<style scoped>
    .check {
        color:red
    }
    .list-move {transition: 1s;}
    .list-enter-active,.list-leave-active {transition: .3s;}
    .list-enter {opacity: 0;transform: translateY(10px)}
    .list-leave-to {opacity: 0;transform: translateY(10px)}
    .list-leave-active {position: absolute}
</style>