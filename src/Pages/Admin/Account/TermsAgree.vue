<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <terms-agree
          :as-admin="true"
          :general-agreed="generalAgreed"
          :marketing-agreed="marketingAgreed"
        ></terms-agree>
      </div>
    </div>
  </div>
</template>

<script>
import {TermsAgree} from 'bedrock-users-vue';

export default {
  components: {
    TermsAgree,
  },

  props: {
    generalAgreed: Boolean,
    marketingAgreed: Boolean,
  },
};
</script>
