<template>
  <div>
    <h1>{{head}}</h1>

    <div class="m-3">
      <h5>Create new money beggar with the form below:</h5>
      <div class="form-row align-items-center">

        <div class="col-auto">
          <input
              type="text"
              class="form-control mb-2"
              placeholder="Beggar name"
              v-model.trim="name"
          >
        </div>

        <div class="col-auto">
          <div class="input-group mb-2">
            <div class="input-group-prepend">
              <div class="input-group-text">Purpose</div>
            </div>
            <select
                class="form-control"
                id="purpose"
                v-model="purpose"
            >
              <option>Birthday gift</option>
              <option>Lunch</option>
              <option>Business</option>
              <option>Shashel</option>
            </select>
          </div>
        </div>

        <div class="col-auto">
          <div class="input-group mb-2">
            <input
              type="text"
              class="form-control"
              placeholder="Desired amount"
              v-model.number="amount"
            >
            <div class="input-group-postpone">
              <div class="input-group-text">$</div>
            </div>
          </div>
        </div>

        <div class="col-auto">
          <div class="form-check mb-2">
            <input class="form-check-input" type="checkbox" id="autoSizingCheck">
            <label class="form-check-label" for="autoSizingCheck">
              Stop begging after achieving goal
            </label>
          </div>
        </div>

        <div class="col-auto">
          <button
              class="btn btn-primary mb-2"
              @click="addBeg"
          >
            Submit
          </button>
        </div>
      </div>
    </div>

    <hr>

    <ul v-if="getBegs">
      <beg
          class="mb-2"
          v-for="beg in begs"
          :key=beg.id
          :begData=beg
          @remove="removeBeg"
      />
    </ul>
  </div>
</template>

<script>
import Beg from "@/components/Beg";

let begId = 1;

export default {
  name: "Beggar",
  components: {
    Beg,
  },
  props: {
    head: String
  },
  data () {
    return {
      name: '',
      purpose: '',
      amount: '',
      begs: []
    }
  },
  computed: {
    getNewBeg: function () {
      return {
        name: this.name,
        purpose: this.purpose,
        amount: this.amount,
      }
    }
  },
  methods: {
    addBeg () {
      const newBeg = this.getNewBeg;
      if (!newBeg.id) {
        newBeg.id = begId++;
        this.begs.push(this.getNewBeg);
        localStorage.setItem('begs', JSON.stringify(this.begs));
        console.log(localStorage.getItem('begs'));
      }
    },
    getBegs() {
      if (!this.begs.length) {
        this.begs = JSON.parse(localStorage.getItem('begs'));
      }
    },
    removeBeg (id) {
      this.begs = this.begs.filter(beg => {
        return beg.id !== id
      })
    }
  }
}
</script>

<style scoped>

</style>