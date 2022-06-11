<template lang="pug">
  .header
    .container
      .logo-wrapper
        img.logo(src="~/assets/img/logo.svg")
      .my-account
        a.account(href='#' @click="show = !show") Мой аккаунт
          .dropdown(v-if="show")
            ul.list
              li.item Настройки
              li.item Выйти
              li.item Верификация
          p(v-else)
</template>

<script>
export default {
  name: 'Header',
  components: {

  },
  data: function(){
    return{
      show: false
    }
  },
  methods: {
    show(){

    }
  }
}
</script>

<style>

</style>
