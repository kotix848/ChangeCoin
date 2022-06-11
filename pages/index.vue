<template lang="pug">
  div
    Header
    .content
      leftNav(:leftMenu="leftMenu" :contacts="leftMenuContacts")
      Exchange(:valut="api")

</template>

<script>
import Exchange from "~/components/lauout/exchange";
import Header from '~/components/lauout/header.vue'
import leftNav from '~/components/lauout/leftNav.vue'

export default {
  name: 'IndexPage',
  components: {
    Header,
    leftNav,
    Exchange
  },
  data() {
    return {
      api: [],
      leftMenu: [
        {title: 'Мой кошелёк'},
        {title: 'Накопительный счёт'},
        {title: 'Мгновенный займ'},
        {title: 'Кредиты'},
        {title: 'Обмен'},
        {title: 'Пригласите друга'},
      ],
      leftMenuContacts: [
        {title: 'Вопросы и ответы'},
        {title: 'Тарифы'},
        {title: 'Политика конфиденциальности'},
        {title: 'Условия использования'},
        {title: 'Регламент GDPR'},
        {title: 'Политика AML'},
      ]
    }
  },
  methods: {},
  mounted() {
    this.$axios
      .get(`https://62a33b0f5bd3609cee660ea0.mockapi.io/api/change/api`)
    .then((r) => {
      this.api = r.data
    })
  }
}
</script>

<style lang="scss">

@import "assets/scss/_variable.scss";
@import "assets/scss/components/header";
@import "assets/scss/components/leftNav";
@import "assets/scss/components/exchange";
@import "../assets/scss/components/formChange";

* {
  margin: 0;
  padding: 0;
  font-family: BlinkMacSystemFont, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
}

a {
  text-decoration: none;
  color: inherit;
}

.container {
  margin: auto;
  width: $container;
}

.content {
  display: flex;
}

</style>
