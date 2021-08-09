<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <plan-features-overview
          :all-features="allFeatures"
          :plan-features="planFeatures"
          :title="$t('bedrock-users::features.title')"
        ></plan-features-overview>
      </div>
    </div>
  </div>
</template>

<script>
import {PlanFeaturesOverview} from 'bedrock-users-vue';

export default {
  components: {
    PlanFeaturesOverview,
  },
  props: {
    allFeatures: Array,
    planFeatures: Array,
  },
};
</script>
