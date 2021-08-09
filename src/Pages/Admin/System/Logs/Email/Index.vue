<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <log-activity-emails :datatable-values="sentEmails" :with-user="true"></log-activity-emails>
      </div>
    </div>
  </div>
</template>

<script>
import {LogActivityEmails} from 'bedrock-users-vue';

export default {
  components: {
    LogActivityEmails,
  },
  props: {
    sentEmails: Array,
  },
};
</script>
