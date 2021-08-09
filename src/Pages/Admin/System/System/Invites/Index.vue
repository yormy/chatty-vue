<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <invite-codes-index :invites="invites"></invite-codes-index>
      </div>
    </div>
  </div>
</template>

<script>
import {InviteCodesIndex} from 'bedrock-users-vue';

export default {
  components: {
    InviteCodesIndex,
  },
  props: {
    invites: Array,
  },
};
</script>
