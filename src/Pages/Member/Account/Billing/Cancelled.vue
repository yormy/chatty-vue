<template>
  <div class="container">
    <h3>
      {{ $t('bedrock-users.billing.subscription.cancelled', {plan: planName}) }}
    </h3>

    <div v-if="featureListHtml">
      {{ $t('bedrock-users.billing.subscription.disallowed_features') }}
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

    featureListHtml: {
      type: String,
    },
  },
};
</script>
