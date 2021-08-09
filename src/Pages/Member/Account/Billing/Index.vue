<template>
  <div class="container">
    <!--    <div class="alert alert-info">{{ session('message') }}</div>-->
    <div class="card">
      <div class="card-body">
        <billing
          :current-plan-id="currentPlanId"
          :discount-enabled="discountEnabled"
          :monthly-plans="monthlyPlans"
          :on-grace-period="onGracePeriod"
          :plan-ends-at="planEndsAt"
          :trial-ends-at="trialEndsAt"
          :yearly-plans="yearlyPlans"
        >
        </billing>
      </div>
    </div>
  </div>
</template>
<!--@section('footer-js')-->
<!--<script src="https://js.stripe.com/v3/"></script>-->
<!--@endsection-->

<script>
import {Billing} from 'bedrock-users-vue';

export default {
  components: {
    Billing,
  },

  props: {
    currentPlanId: String,
    monthlyPlans: Array,
    onGracePeriod: Boolean,
    planEndsAt: String,
    trialEndsAt: String,
    yearlyPlans: Array,
    discountEnabled: Boolean,
  },
};
</script>
