<template>
  <div>
    <auto-logout v-if="config.autologoutEnabled" logged-in-as="MEMBER"></auto-logout>
    <div class="container-scroller">
      <topbar></topbar>
      <div class="container-fluid page-body-wrapper">
        <sidebar></sidebar>

        <div class="main-panel">
          <top-warnings-spacer></top-warnings-spacer>
          <impersonated-spacer></impersonated-spacer>
          <div class="content-wrapper">
            <v-app>
              <div style="min-height: auto !important; width: inherit">
                <impersonated-spacer></impersonated-spacer>
                <actions-required></actions-required>
                member-layout == topbar vue You are logged in as
                <!--                <sidebar-mini></sidebar-mini>-->
                <breadcrumb :breadcrumbs="breadcrumbs"></breadcrumb>

                <br />
                <slot />
              </div>
            </v-app>
          </div>

          <footer-bar></footer-bar>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Topbar from './Partials/Topbar.vue';
import TopWarningsSpacer from './Partials/TopWarningsSpacer.vue';
import Sidebar from './Partials/Sidebar.vue';
import FooterBar from './Partials/FooterBar.vue';
import Breadcrumb from './Partials/Breadcrumb.vue';
import ImpersonatedSpacer from "./Partials/ImpersonatedSpacer.vue";
import ActionsRequired from "./Partials/ActionsRequired.vue";
import {AutoLogout} from "bedrock-users-vue";

// import SidebarMini from './Partials/SidebarMini.vue';

export default {
  components: {
    ImpersonatedSpacer,
    Breadcrumb,
    Topbar,
    TopWarningsSpacer,
    Sidebar,
    FooterBar,
    ActionsRequired,
    AutoLogout
    // SidebarMini,
  },

  props: {
    breadcrumbs: {
      type: Array,
      required: false,
      default() {
        return []
      }
    },
  },

  data() {
    return {
      config: this.$page.props.site.config,
    };
  },
};
</script>
<style>
.v-application--wrap {
  min-height: inherit !important;
}
</style>
