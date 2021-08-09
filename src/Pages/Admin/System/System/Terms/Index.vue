<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <terms-management :datatable-values="terms"></terms-management>
      </div>
    </div>
  </div>
</template>

<script>
import {TermsManagement} from 'bedrock-users-vue';

export default {
  components: {
    TermsManagement,
  },

  props: {
    terms: Array,
  },
};
</script>
