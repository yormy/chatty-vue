<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <payment-methods
          :api-key="apiKey"
          :client-secret="clientSecret"
          :default-payment-method-id="defaultPaymentMethodId"
          :payment-methods="paymentMethods"
        >
        </payment-methods>
      </div>
    </div>
  </div>
</template>

<script>
import {PaymentMethods} from 'bedrock-users-vue';

export default {
  components: {
    PaymentMethods,
  },

  props: {
    paymentMethods: {
      type: Array,
      required: true,
    },

    defaultPaymentMethodId: {
      type: String,
      required: true,
    },

    clientSecret: {
      type: String,
      required: true,
    },

    apiKey: {
      type: String,
      required: true,
    },
  },
};
</script>
