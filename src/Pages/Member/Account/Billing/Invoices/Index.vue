<template>
  <div class="card">
    <div class="card-body">
      <invoices :payments="payments"></invoices>
    </div>
  </div>
</template>

<script>
import {Invoices} from 'bedrock-users-vue';

export default {
  components: {
    Invoices,
  },

  props: {
    payments: Array,
  },
};
</script>
