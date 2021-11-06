<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <teams-index
          :datatable-values="teams"
          :title="$t('bedrock-users.admin.index.title')"
        ></teams-index>
      </div>

      <div class="card-body">
        <invites-received
          :datatable-values="invitesReceivedActions"
          :title="$t('bedrock-users.admin.index.title')"
        ></invites-received>
      </div>
    </div>
  </div>
</template>

<script>
import {InvitesReceived, TeamsIndex} from 'bedrock-users-vue';

export default {
  components: {
    TeamsIndex,
    InvitesReceived
  },

  props: {
    teams: Array,

    invitesReceivedActions: {
      type: Array,
      required: true,
    }
  },
};
</script>
