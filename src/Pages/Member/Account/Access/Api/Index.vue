<template>
  <div class="container">
    <!--    <div class="alert alert-info">{{ session('message') }}</div>-->
    <div class="card">
      <card-header :title="$t('bedrock-users.account.access.api.title')"></card-header>
      <div class="card-body">
        <div v-if="form.token">
          <strong>{{ $t('bedrock-users.account.access.api.your_new_key') }}</strong>
          <success-message
            :message="$t('bedrock-users.account.access.api.copied')"></success-message>
          {{ form.token }}
        </div>

        <button-submit
          v-else
          :is-loading="form.state.isSubmittingAdd"
          btn-class="btn btn-danger float-right"
          @click="generateKey()"
        >
          {{ $t('bedrock-users.account.access.api.generate') }}
          generate
        </button-submit>
      </div>
    </div>

    <div class="card">
      <div class="card-body">

        <strong>{{ $t('bedrock-users.account.access.api.current_keys') }}</strong>
        <table class="table table-borderless table-condensed">
          <thead>
          <tr>
            <td>#</td>
            <td>{{ $t('bedrock-core.general.created_at') }}</td>
          </tr>
          </thead>
          <tbody>

          <tr v-for="accessToken in currentAccessTokens" :key="accessToken.id">
            <td>{{ accessToken.short_id }}</td>
            <td>{{ accessToken.created_at_human }}</td>
            <td>
              <button-delete :item="accessToken" @deleteItem="deleteAgreed(accessToken)">
              </button-delete>
            </td>
          </tr>
          </tbody>
        </table>

      </div>
    </div>
  </div>
</template>
<!--@section('footer-js')-->
<!--<script src="https://js.stripe.com/v3/"></script>-->
<!--@endsection-->

<script>
import {ButtonDelete, CardHeader} from "bedrock-core-vue";

export default {
  components: {
    CardHeader,
    ButtonDelete
  },

  props: {
    // currentPlanId: String,
    accessTokens: Array,
    // onGracePeriod: Boolean,
    // planEndsAt: String,
    // trialEndsAt: String,
    // yearlyPlans: Array,
    // discountEnabled: Boolean,
  },


  data() {
    return {
      form: {
        state: {
          isSubmittingAdd: false,
        },


        token: '',

        messages: {
          success: '',
          warning: '',
          error: '',
        },

        apiErrors: {},
      },

      currentAccessTokens: this.accessTokens,

      routes: {
        generate: 'api.v1.member.account.access.api.generate',
        delete: 'api.v1.member.account.access.api.destroy',
      }

    };
  },

  methods: {
    generateKey() {
      this.form.state.isSubmittingAdd = true;

      const url = this.route(this.routes.generate);

      this.$http
        .post(url)
        .then(response => {
          this.form.token = response.data.data;
          this.copyClipboard(this.form.token);
        })
        .catch(error => {
        })
        .finally(() => {
          this.form.state.isSubmittingAdd = false;
        });
    },

    deleteAgreed(accessToken) {
      const url = this.route(this.routes.delete, accessToken.id);
      this.$http
        .delete(url)
        .then(response => {
          this.currentAccessTokens = response.data.data;
        })
        .catch(error => {
        })
        .finally(() => {

        });
    },

    copyClipboard(value) {
      const self = this;
      navigator.clipboard.writeText(value).then(function () {
        self.valueOnClipboard = value;
      }, function (err) {
        console.error('Could not copy text: ', err);
      });
    },

  }
};
</script>
