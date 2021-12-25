<template>
  <div>
    <div id="loginform">
      <div class="">
        <div class="row">
          <div class="col-12">
            <registration
              :action="confirmableAction"
              :continue-registration-xid="continueRegistrationXid"
              :current-step="currentStep"
              :error="error"
              :invite-code-setting="registration.inviteCode"
              :phone-mandatory="registration.phoneMandatory"
              :sent-to-email-prop="sentToEmail"
              :sent-to-phone-prop="sentToPhone"
            >
            </registration>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {Registration} from 'bedrock-users-vue';
import Right from '../../../Layouts/Member/Login.vue';

export default {
  metaInfo() {
    return {title: ''};
  },

  layout: Right,

  components: {
    Registration,
  },

  props: {
    continueRegistrationXid: String,
    currentStep: String,
    sentToEmail: String,
    sentToPhone: String,
    error: Array,
    confirmableAction: {
      type: Object,
      required: false,
    }
  },

  data() {
    return {
      branding: this.$page.props.shared.branding,
      registration: this.$page.props.shared.registration,
    };
  },
};
</script>
