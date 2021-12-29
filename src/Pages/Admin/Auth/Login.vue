<template>
  <div id="loginform">
    <div class="">
      <div class="row">
        <div class="col-12">
          ADMIN LOGIN
          <login-wrapper
            :as-admin="true"
            :token-error-message="tokenErrorMessage"
            :token-ip-whitelisting="tokenIpWhitelisting"
          >
          </login-wrapper>
        </div>
      </div>

      <div class="wrapper mt-5 text-gray text-center" style="">
        <p class="footer-text">
          {{ branding.copyright }}
        </p>
        <ul class="auth-footer text-gray justify-content-center">
          <li>
            <a :href="route('guest.terms.general')" target="_blank">
              {{ $t('bedrock-users.login.terms.title') }}
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import {LoginWrapper} from 'bedrock-users-vue';
import LayoutAdminLogin from '../../../Layouts/Admin/Center';

export default {
  metaInfo: {title: 'Login1111'},
  layout: LayoutAdminLogin,
  components: {
    LoginWrapper,
  },

  props: {
    token: String,
    tokenErrorMessage: String,
    allowRegistration: Boolean,
    tokenIpWhitelisting: String,
  },

  data() {
    return {
      branding: this.$page.props.site.branding,
    };
  },
};
</script>
