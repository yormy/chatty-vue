<template>
  <div class="container">
    <h3>
      {{ planName }}
      {{ $t('bedrock-users.billing.success.your_new_plan', {plan: planName}) }}
    </h3>

    <div v-if="trialEndsAt" class="alert alert-info">
      {{ $t('bedrock-users.billing.subscription.trial_ends_at', {date: trialEndsAt}) }}
    </div>

    <div v-if="featureListHtml">
      {{ $t('bedrock-users.billing.subscription.allowed_features') }}
      <!--eslint-disable-next-line vue/no-v-html-->
      <div v-html="featureListHtml"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    planName: {
      type: String,
      required: true,
    },

    trialEndsAt: {
      type: String,
    },

    featureListHtml: {
      type: String,
    },
  },
};
</script>
