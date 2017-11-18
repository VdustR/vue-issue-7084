<template lang="pug">
#app
  my-radio(:value="true" v-model="value") true
  my-radio(:value="false" v-model="value") false
  my-radio(value="abc" v-model="value") "abc"
  my-radio(v-model="value") <i>nothing</i>
  my-radio(v-model="value") <i>nothing</i>
  div value: {{value}}
</template>

<script>
import Vue from 'vue'

export default {
  data () {
    return {
      value: null
    }
  },
  components: {
    myRadio: {
      name: 'myRadio',
      props: {
        model: [String, Number, Boolean],
        value: {
          type: [String, Number, Boolean],
          default: 'on'
        }
      },
      model: {
        prop: 'model',
        event: 'change'
      },
      computed: {
        checked () {
          return this.model === this.value
        }
      },
      methods: {
        toggle () {
          this.$emit('change', this.value)
        }
      },
      template: `
        <label @click.prevent="toggle">
          <input type="radio" v-bind="{ value, checked }" />
          <slot></slot>
        </label>
      `
    }
  }
}
</script>
