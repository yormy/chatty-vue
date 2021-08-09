<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <user-notify :billing-plans="billingPlans" :placeholders="placeholders"></user-notify>
      </div>
    </div>
  </div>
</template>

<script>
import {UserNotify} from 'bedrock-users-vue';

export default {
  components: {
    UserNotify,
  },

  props: {
    billingPlans: Array,
    placeholders: Array,
  },
};
</script>
