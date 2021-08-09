<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <my-notifications :as-admin="true" :datatable-values="notifications"></my-notifications>
      </div>
    </div>
  </div>
</template>

<script>
import {MyNotifications} from 'bedrock-users-vue';

export default {
  components: {
    MyNotifications,
  },

  props: {
    notifications: Array,
  },
};
</script>
