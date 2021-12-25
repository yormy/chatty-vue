<template>
  <div class="card-body">
    <confirm-action
      :confirm-description="confirmableAction.description"
      :confirm-sent-to="sentToEmail"
      :confirm-title="confirmableAction.title"
      :method="confirmableAction.method"
      :verify-action-url="route('api.v1.guest.verify.verify')"
      :verify-resend-action-url="route('api.v1.guest.verify.resend')"
      :xid="confirmableAction.xid"
      verify-type="CODE"
      @verified="verified"
    >
    </confirm-action>
  </div>
</template>

<script>
import LayoutGuestRight from '../../Layouts/Guest/Right';
import {ConfirmAction} from 'bedrock-users-vue';

export default {
  layout: LayoutGuestRight,

  components: {
    ConfirmAction
  },

  props: {
    confirmableAction: {
      type: Object,
      required: true,
    },

    sentToEmail: {
      type: String,
      required: false,
    },
  },

  data() {
    return {};
  },

  methods: {
    verified() {
      this.$emit('verified');
    },
  },
};
</script>
