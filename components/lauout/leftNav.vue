<template lang="pug">
  .leftMenu
    .container
      .top
        ul.list
          li(v-for="item of leftMenu").item {{ item.title }}


        .language
          select().select-language
            option Русский
            option Английский
      .bottom
        .contacts Контакты <br>
          a(href="#mail") support@coinloan.io

          ul.list
            a.item(href="#contact" v-for="item of contacts").item {{ item.title }} <br>
</template>

<script>
export default {
  name: 'leftNav',
  props: ['leftMenu', 'contacts']
}
</script>
