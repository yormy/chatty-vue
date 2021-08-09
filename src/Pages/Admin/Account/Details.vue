<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <my-details
          :active-sessions="activeSessions"
          :as-admin="true"
          :authenticator-enabled="authenticatorEnabled"
          :current-session="currentSession"
          :sent-emails="sentEmails"
          :timezones="timezones"
          :user="user"
          :whitelisted-browsers="browserTokens"
          :whitelisted-ips="ipAddresses"
        ></my-details>
      </div>
    </div>
  </div>
</template>

<script>
import {MyDetails} from 'bedrock-users-vue';

export default {
  components: {
    MyDetails,
  },

  props: {
    activeSessions: Array,
    authenticatorEnabled: Boolean,
    browserTokens: Array,
    currentSession: String,
    ipAddresses: Array,
    sentEmails: Array,
    timezones: Array,
    user: Object,
  },
};
</script>
