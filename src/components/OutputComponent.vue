
<template>
    <div>
        <EqualComponent @inputData="(data) => this.outputInputs = data"
                        @signData="(data) => this.outputSigns = data"
                        @answer="(data) => this.answer = data"
        />


        <!-- {{ outputInputs[0] }} {{ outputSigns[0] }} {{ outputInputs[1] }} {{ outputSigns[1] }} {{ outputInputs[2] }} = {{ answer }} -->
        <AnimatedCounter v-bind:number="outputInputs[0]" /> {{ outputSigns[0] }}
        <AnimatedCounter v-bind:number="outputInputs[1]" /> {{ outputSigns[1] }}
        <AnimatedCounter v-bind:number="outputInputs[2]" /> = <AnimatedCounter v-bind:number="answer" />
      </div>
</template>

<script>
import EqualComponent from '@/components/EqualComponent.vue'
import AnimatedCounter from '@/components/AnimatedCounter.vue'
export default {
    name: 'OutputComponent',
    components: {
    EqualComponent,
    AnimatedCounter
  },
    data () {
        return {
            outputInputs: [0,0,0],
            outputSigns: ['+','+'],
            answer: 0
        }
    },
 
}



</script>
<style>
    
</style>