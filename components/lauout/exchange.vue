<template lang="pug">
  .exchange
    p.title Обмен валют
    .change
      p.title Обменять USD на RUB
      FormChange(:valut="valut")
</template>


<script lang="js">
import FormChange from "~/components/lauout/formChange";
export default {
  components: {FormChange},
  props: ['valut']
}
</script>
