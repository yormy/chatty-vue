<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <reverify-phone :as-admin="true" :authenticator-enabled="authenticatorEnabled" :user="user">
        </reverify-phone>
      </div>
    </div>
  </div>
</template>

<script>
import {ReverifyPhone} from 'bedrock-users-vue';

export default {
  components: {
    ReverifyPhone,
  },

  props: {
    user: Object,
    authenticatorEnabled: Boolean,
  },
};
</script>
