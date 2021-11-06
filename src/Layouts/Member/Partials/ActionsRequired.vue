<template>
  <div v-if="confirmableActions">

    <div v-for="action in confirmableActions" :class="'alert alert-info'"
         style="overflow-wrap: break-word">
      <div class="d-flex justify-content-between">
        <div>
          <strong>{{ action.title }}</strong>
        </div>
        <div>
          <a :href="action.ctaUrl">
            <button class="btn btn-primary">{{ action.ctaLabel }}</button>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      confirmableActions: this.$page.props.shared.confirmableActions,
    };
  },
};
</script>

