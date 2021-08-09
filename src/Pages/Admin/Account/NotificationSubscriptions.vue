<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <my-notification-settings
          :as-admin="true"
          :mail-templates="subscriptions"
        ></my-notification-settings>
      </div>
    </div>
  </div>
</template>

<script>
import {MyNotificationSettings} from 'bedrock-users-vue';

export default {
  components: {
    MyNotificationSettings,
  },

  props: {
    subscriptions: Array,
  },
};
</script>
