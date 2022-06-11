<template lang="pug">
  div
    label Вы отдаёте <br>
    input.input
    button(@click="baseCheck = !baseCheck" v-model="base" class="button") {{ base }}
    .dropdown-base(v-if="baseCheck")
      ul.list
        a.item( href="#"  v-for="val of valut") {{ val.base_currency }} <br>
    p(v-else)
    p.post-title Доступно 0 {{ base }}

    label Вы получаете <br>
    input.input
    button(@click="quoteCheck = !quoteCheck" v-model="quote" class="button") {{ quote }}
    .dropdown-base(v-if="quoteCheck")
      ul.list
        a.item( href="#" v-model="quote" v-for="val of valut") {{ val.quote_currency }} <br>
    p(v-else)
    p.post-title Доступно 0 {{ quote }}
</template>


<script lang="js">
export default {
  props: ['valut'],
  data: function(){
    return{
      baseCheck: false,
      quoteCheck: false,
      base: 'RUB',
      quote: 'USD',
      pair: '',
    }
  },
  methods: {
    baseCheck(){

    },
    quoteCheck(){

    },
    base(){

    },
    quote(){

    }
  }
}
</script>
