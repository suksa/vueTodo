<template>
    <div>
        <input type="text" v-model="input" v-on:keyup.enter="dataInsert">
        <button @click="dataInsert">submit</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                input: ''
            }
        },
        methods:{
            dataInsert(){
                this.$emit('dataInsert',this.input)
                this.cleartInput()
            },
            cleartInput(){
                this.input = ''
            }
        }
    }
</script>

<style scoped>

</style>