<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <invite-code-edit :model="inviteCode"></invite-code-edit>
      </div>
    </div>
  </div>
</template>

<script>
import {InviteCodeEdit} from 'bedrock-users-vue';

export default {
  components: {
    InviteCodeEdit,
  },
  props: {
    inviteCode: Object,
  },
};
</script>
