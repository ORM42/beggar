<template>
  <li>
    <button @click="$emit('remove', sponsor.id)">
      x
    </button>
    {{ sponsor.text }}
    <input
        type="text"
        :value="value"
        v-on="enter"
    >
    <button
        class="btn btn-primary btn-sm"
        @click="$emit('pay', value)"
    >
      v
    </button>
  </li>
</template>

<script>
export default {
  props: {
    sponsor: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      value: '',
    }
  },
  computed: {
    enter () {
      return {
        input: event => this.value = event.target.value
      }
    }
  }
}
</script>

<style scoped>

</style>