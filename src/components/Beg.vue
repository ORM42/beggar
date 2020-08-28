<template>
  <div class="card">
    <div class="card-header">Title: <b>{{ begData.name }}</b></div>
    <div class="card-body">
      <span>{{ begData.purpose }} ({{ begData.amount }})</span>
      <hr/>
      <ul v-if="sponsors.length">
        <sponsor
            v-for="sponsor in sponsors"
            :key="sponsor.id"
            :name="sponsor.name"
            @remove="removeSponsor"
        />
      </ul>
      <input
          placeholder="Add a new sponsor"
          v-else
      >
    </div>
    <div class="card-footer">Total amount:</div>
  </div>
</template>

<script>
import Sponsor from "@/components/Sponsor";

export default {
  components: {
    Sponsor,
  },
  props: {
    begData: {
      type: Object,
      required: true
    },
  },
  data () {
    return {
      sponsors: []
    }
  }
}
</script>

<style scoped>

</style>