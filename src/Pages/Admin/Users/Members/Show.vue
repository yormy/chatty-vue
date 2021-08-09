<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <user-details
          :active-sessions="activeSessions"
          :activities="activities"
          :agreements="agreements"
          :as-admin-management="true"
          :audits="audits"
          :firewall-logs="firewallLogs"
          :permissions="permissions"
          :security="security"
          :sent-emails="sentEmails"
          :standby="standby"
          :standby-dict="standbyDict"
          :statistics="statistics"
          :user="user"
        ></user-details>
      </div>
    </div>
  </div>
</template>

<script>
import {UserDetails} from 'bedrock-users-vue';

export default {
  components: {
    UserDetails,
  },

  props: {
    activeSessions: Array,
    activities: Array,
    agreements: Array,
    audits: Array,
    firewallLogs: Array,
    permissions: Array,
    security: Object,
    sentEmails: Array,
    standby: Array,
    standbyDict: Array,
    statistics: Object,
    user: Object,
  },
};
</script>
