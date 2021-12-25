<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-header">Welcome Admin Dashboard</div>
      <div class="card-body">
        <admin-dashboard
          :activities="activities"
          :audits="audits"
          :counts="counts"
          :emails-recent="emailsRecent"
          :registrations="registrations"
          :registrations-expired="registrationsExpired"
          :subscriptions-cancellations="subscriptionsCancellations"
          :subscriptions-ending="subscriptionsEnding"
          :subscriptions-new="subscriptionsNew"
          :users="users"
        >
        </admin-dashboard>
      </div>
    </div>
  </div>
</template>

<script>
import {AdminDashboard} from 'bedrock-users-vue';

export default {
  components: {
    AdminDashboard,
  },

  props: {
    activities: Array,
    audits: Array,
    counts: Object,
    emailsRecent: Array,
    registrations: Array,
    registrationsExpired: Array,
    subscriptionsCancellations: Array,
    subscriptionsEnding: Array,
    subscriptionsNew: Array,
    users: Array,
  },
};
</script>
