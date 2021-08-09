<template>
  <div class="container mw-100">
    <admin-security-details
      :action-tarpits="actionTarpits"
      :blacklisted-emails="blacklistedEmails"
      :blacklisted-ips="blacklistedIps"
      :firewall-ips="firewallIps"
      :firewall-logs="firewallLogs"
      :firewall-tarpits="firewallTarpits"
    ></admin-security-details>
  </div>
</template>

<script>
import {AdminSecurityDetails} from 'bedrock-users-vue';

export default {
  components: {
    AdminSecurityDetails,
  },

  props: {
    firewallLogs: Array,
    firewallTarpits: Array,
    firewallIps: Array,
    blacklistedEmails: Array,
    blacklistedIps: Array,
    actionTarpits: Array,
  },
};
</script>
