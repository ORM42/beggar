<template>
  <div class="card">
    <div class="card-header">
      Title: <b>{{ begData.name }} ({{ begData.amount }}$ for {{ begData.purpose }})</b>
      <button
          class="float-right"
          @click="$emit('remove', begData.id)"
      >X</button>
    </div>
    <div class="card-body">
      <ul v-if="sponsors.length">
        <sponsor
            v-for="sponsor in sponsors"
            :key="sponsor.id"
            :sponsor="sponsor"
            @pay="addMoney"
            @remove="delSponsor"
        />
      </ul>
      <hr/>
      <add-sponsor
          placeholder="Add a new sponsor"
          v-model.trim="moneyBag"
          @keyup.enter="addSponsor"
      />
    </div>
    <div class="card-footer">Total amount: {{total}}</div>
  </div>
</template>

<script>
import AddSponsor from "@/components/AddSponsor";
import Sponsor from "@/components/Sponsor";

let sponsorId = 1;

export default {
  components: {
    Sponsor,
    AddSponsor,
  },
  props: {
    begData: {
      type: Object,
      required: true
    },
  },
  data () {
    return {
      moneyBag: '',
      sponsors: [],
      total: 0
    }
  },
  methods: {
    addSponsor () {
      if (this.moneyBag) {
        this.sponsors.push({
          id: sponsorId++,
          text: this.moneyBag,
          money: ''
        })
        this.moneyBag = ''
      }
    },
    addMoney (amount) {
      this.total += parseInt(amount)
    },
    delSponsor (sponsorId) {
      this.sponsors = this.sponsors.filter(sponsor => {
        return sponsor.id !== sponsorId
      })
    }
  }
}
</script>

<style scoped>

</style>