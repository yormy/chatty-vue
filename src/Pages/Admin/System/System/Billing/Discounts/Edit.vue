<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <discount-code-edit :model="discountCode"></discount-code-edit>
      </div>
    </div>
  </div>
</template>

<script>
import {DiscountCodeEdit} from 'bedrock-users-vue';

export default {
  components: {
    DiscountCodeEdit,
  },
  props: {
    discountCode: Object,
  },
};
</script>
