<template>
  <div>
    <div id="loginform">
      <div class="">
        <div class="row">
          <div class="col-12">
            <login-wrapper
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
  </div>
</template>

<script>
import {LoginWrapper} from 'bedrock-users-vue';
import LayoutMemberLogin from '../../../Layouts/Member/Login';

export default {
  metaInfo: {title: 'Login Chatty'},
  layout: LayoutMemberLogin,
  components: {
    LoginWrapper,
  },

  props: {
    token: String,
    tokenErrorMessage: String,
    tokenIpWhitelisting: String,
  },

  data() {
    return {
      branding: this.$page.props.site.branding,
    };
  },
};
</script>
