<template>
  <div>
    <loading-overlay :show="form.state.isSubmitting"></loading-overlay>

    <div class="form-horizontal">
      <div class="form-group">
        <messages :messages="form.messages"></messages>
      </div>
    </div>

    <!--    <div class="card card-table">-->
    <!--      <v-tabs-->
    <!--        v-model="tab"-->
    <!--        :grow="true"-->
    <!--        :icons-and-text="true"-->
    <!--        background-color="bg-info"-->
    <!--        class="elevation-2"-->
    <!--        dark-->
    <!--      >-->
    <!--        <v-tabs-slider></v-tabs-slider>-->

    <!--        <v-tab :href="`#tab-branding`">-->
    <!--          &lt;!&ndash;          {{ $t('bedrock-users.my_details.personal.title') }}&ndash;&gt;-->
    <!--          branding-->
    <!--          <i class="fal fa-home fa-2x"></i>-->
    <!--        </v-tab>-->

    <!--        <v-tab :href="`#tab-user`">-->
    <!--          &lt;!&ndash;          {{ $t('bedrock-users.my_details.personal.title') }}&ndash;&gt;-->
    <!--          registration-->
    <!--          <i class="fal fa-user-cog fa-2x"></i>-->
    <!--        </v-tab>-->

    <!--        <v-tab :href="`#tab-billing`">-->
    <!--          &lt;!&ndash;          {{ $t('bedrock-users.my_details.personal.title') }}&ndash;&gt;-->
    <!--          billing-->
    <!--          <i class="fal fa-home fa-2x"></i>-->
    <!--        </v-tab>-->

    <!--        <v-tab :href="`#tab-chatty`">-->
    <!--          chatty-->
    <!--          <i class="fal fa-chart-scatter fa-2x"></i>-->
    <!--        </v-tab>-->

    <!--        <v-tab-item :value="'tab-branding'">-->
    <!--          <branding-settings :settings="settings.branding"></branding-settings>-->
    <!--        </v-tab-item>-->

    <!--        <v-tab-item :value="'tab-user'">-->
    <!--          <registration-settings :settings="settings.registration"></registration-settings>-->
    <!--        </v-tab-item>-->

    <!--        <v-tab-item :value="'tab-billing'">-->
    <!--          <billing-settings :settings="settings.billing"></billing-settings>-->
    <!--        </v-tab-item>-->

    <!--        <v-tab-item :value="'tab-chatty'"> chatty222222</v-tab-item>-->
    </v-tabs>
  </div>
  </div>
</template>

<script>
// import {BillingSettings, RegistrationSettings} from 'bedrock-users-vue';
// import {BrandingSettings} from 'bedrock-core-vue';

export default {
  components: {
    // BrandingSettings,
    // BillingSettings,
    // RegistrationSettings,
  },

  props: {
    title: {
      type: String,
    },
    icon: {
      type: String,
    },
    description: {
      type: String,
    },

    settings: {
      type: Object,
      required: true,
    },
  },

  data: () => ({
    tab: null,

    form: {
      data: {
        name: null,
      },

      state: {
        isSubmitting: null,
      },

      messages: {
        success: '',
        warning: '',
        error: '',
      },

      apiErrors: {},
    },
  }),
};
</script>
