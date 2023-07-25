<template>
    <div class="equalComponent">
        <InputComponent @inputValue="getInput($event, 0)"/> 
        <SignComponent @signValue="getSign($event, 0)"/> 
        <InputComponent @inputValue="getInput($event, 1)"/> 
        <SignComponent @signValue="getSign($event, 1)"/> 
        <InputComponent @inputValue="getInput($event, 2)"/> 
         = {{ answer }}
    </div>
</template>
<script>
import Vue from 'vue';
import InputComponent from './InputComponent.vue';
import SignComponent from './SignComponent.vue';
export default {
    name: 'EqualComponent',
    components: {
    InputComponent,
    SignComponent,
  },
    data () {
        return {
            inputData: ['0','0','0'],
            signData: ['+','+'],
        }
    },
    computed: {
        answer: function () {
            // return this.inputData + this.signData
            return eval(this.inputData[0] + this.signData[0] + this.inputData[1] + this.signData[1] + this.inputData[2])
            
        }
    },
    methods: {
        getInput(data, index) {
            // this.inputData.push(data)
            Vue.set(this.inputData, index, data)
            // console.log(data)
        },
        getSign(data, index) {
            // this.inputData.push(data)
            Vue.set(this.signData, index, data)
            // console.log(data)
        }
    },
    watch: {
        inputData: function(newInputData) {
            this.$emit("inputData", newInputData)
        },
        signData: function(newSignData) {
            this.$emit("signData", newSignData)
        },
        answer: function(newAnswer) {
            this.$emit("answer", newAnswer)
        }
    }
}
</script>
<style>
    .equalComponent {
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
</style>