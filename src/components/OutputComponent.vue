<script src="js/tween/Tween.js"></script>
<template>
    <div>
        <EqualComponent @inputData="(data) => this.outputInputs = data"
                        @signData="(data) => this.outputSigns = data"
                        @answer="(data) => this.answer = data"
              />
        <!-- {{ outputInputs[0] }} {{ outputSigns[0] }} {{ outputInputs[1] }} {{ outputSigns[1] }} {{ outputInputs[2] }} = {{ answer }} -->
        <span class="tweened-number">{{ tweeningValue }}</span>
    </div>
</template>

<script>
import EqualComponent from '@/components/EqualComponent.vue'
export default {
    name: 'OutputComponent',
    components: {
    EqualComponent
  },
    props: {
        // The value that we'll be tweening to.
        value: {
        type: Number,
        required: true
        },

        // How long the tween should take. (In milliseconds.)
        tweenDuration: {
        type: Number,
        default: 500
        }
    },
    watch: {
    // Whenever `props.value` changes, update the tween.
    value(newVal, oldVal) {
      this.tween(oldVal, newVal)
    }
  },
    data () {
        return {
            outputInputs: [0,0,0],
            outputSigns: ['+','+'],
            answer: 0,
            tweeningValue: 0,
            value: 100
        }
    },
    methods: {
    // This is our main logic block. It handles tweening from a start value to an end value.
    tween(start, end) {
      let frameHandler

      // Handles updating the tween on each frame.
      const animate = function (currentTime) {
        TWEEN.update(currentTime)
        frameHandler = requestAnimationFrame(animate)
      }

      const myTween = new TWEEN.Tween({ tweeningValue: start })
      .to({ tweeningValue: end }, this.tweenDuration)
      // Be careful to not to do too much here! It will slow down the app.
      .onUpdate(() => {
        this.tweeningValue = myTween.tweeningValue.toFixed(0)
      })
      .onComplete(() => {
        // Make sure to clean up after ourselves.
        cancelAnimationFrame(frameHandler)
      })
      // This actually starts the tween.
      .start()

      frameHandler = requestAnimationFrame(animate)
    }
  },
 mounted() {
    this.tween(0, this.value)
  },
 
}



</script>
<style>
    
</style>