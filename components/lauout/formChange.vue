<template lang="pug">
  div
    label Вы отдаёте <br>
    input.input(v-model="convertfrom")
    button(@click="baseCheck = !baseCheck" v-model="base" class="button") {{ baseClickGet }}
    .dropdown-base(v-if="baseCheck")
      p.item( href="#"  v-for="val of valut" v-model="baseClickGet" @click="baseClick") {{ val.base_currency }} <br>
    p(v-else)
    p.post-title Доступно 0

    label Вы получаете <br>
    input.input(v-model="finalamount")
    button(@click="quoteCheck = !quoteCheck" v-model="quote" class="button") {{ quoteClickGet }}
    .dropdown-base(v-if="quoteCheck")
      p.item( href="#" v-for="val of valut" v-model="quoteClickGet" @click="quoteClick") {{ val.quote_currency }} <br>
    p(v-else)
    p.post-title Доступно 0

</template>


<script lang="js">
export default {
  props: ['valut'],
  data: function () {
    return {
      baseCheck: false,
      quoteCheck: false,
      base: "",
      quote: "",
      pair: '',
      convertfrom: "",
      convertto: "",
      baseClickGet: "USD ",
      quoteClickGet: "RUB ",
      course: []
    }
  },
  methods: {
    baseCheck() {
      return false
    },
    quoteCheck() {
      return false
    },
    base() {
      return false
    },
    quote() {
      return false
    },
    baseClick(e) {
      this.baseClickGet = e.target.textContent
    },
    quoteClick(e) {
      this.quoteClickGet = e.target.textContent
    },
    baseClickGet() {
      return false
    }
  },
  mounted() {
    this.$axios
      .get(`https://62a33b0f5bd3609cee660ea0.mockapi.io/api/change/exchange`)
      .then(response => this.course = response.data)
  },
  computed: {
    finalamount: function () {
      var from = this.convertfrom;
      var to = this.convertto;
      var lastfrom;
      var lastto;

      if (from) {
        if (this.baseClickGet === "USD " && this.quoteClickGet === "RUB ") {
          lastto = from * 57.85;
          return lastto;
        }
        if(this.baseClickGet === "EUR " && this.quoteClickGet === "RUB "){
          lastto = from * 59.83;
          return lastto;
        }
        if (this.baseClickGet === "USD " && this.quoteClickGet === "EUR ") {
          lastto = from * 0.95;
          return lastto;
        }
        if (this.baseClickGet === "EUR " && this.quoteClickGet === "USD ") {
          lastto = from * 1.05;
          return lastto;
        }
        if (this.baseClickGet === "EUR " && this.quoteClickGet === "USD ") {
          lastto = from * 1.05;
          return lastto;
        }
        if (this.baseClickGet === "RUB " && this.quoteClickGet === "USD ") {
          lastto = from * 0.017;
          return lastto;
        }
        if (this.baseClickGet === "RUB " && this.quoteClickGet === "EUR ") {
          lastto = from * 0.016;
          return lastto;
        }
        if(this.baseClickGet === this.quoteClickGet){
          lastto = from;
          return lastto;
        }
      }
      if (to) {
        lastfrom = to * 21.4;
        return lastfrom;
      }
    },
    rate: function () {
      var cur;
      var base = this.base;
      var quote = this.quote;
      for (cur of this.course) {
        //console.log(cur.rate)
      }
    }
  },
}
</script>
