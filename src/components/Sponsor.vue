<template>
  <div>
      <input
          type="text"
          class="form-control"
          placeholder={{placeholder}}
          :value="value"
          v-on=""
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
    title: String,
    placeholder: String,
  }
}
</script>

<style lang="scss" scoped>

</style>