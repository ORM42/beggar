<template>
  <div>
      <input
          type="text"
          class="form-control"
          placeholder="Add a new sponsor"
          :value="value"
          v-on="enter"
      >
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    },
  },
  computed: {
    enter () {
      return {
        ...this.$listeners,
        input: event => this.$emit('input', event.target.value)
      }
    }
  }
}
</script>

<style lang="scss" scoped>

</style>