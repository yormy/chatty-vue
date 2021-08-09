<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <discount-codes-index :discount-codes="discountCodes"></discount-codes-index>
      </div>
    </div>
  </div>
</template>

<script>
import {DiscountCodesIndex} from 'bedrock-users-vue';

export default {
  components: {
    DiscountCodesIndex,
  },
  props: {
    discountCodes: {
      type: Array,
      required: true,
    },
  },
};
</script>
