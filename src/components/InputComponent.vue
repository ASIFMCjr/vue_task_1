<template>
    <div>
        <input 
        :value = "inputValue" 
        v-on:input="changeValue"
        type="number" 
        placeholder="число" />
        {{ inputValue }}
    </div>
</template>
<script>
export default {
    name: 'InputComponent',
    data () {
        return {
            inputValue: 0
        }
    },
    methods: {
        changeValue(event) {
            this.inputValue = event.target.value
        }
    }
}
</script>
<style>
    
</style>