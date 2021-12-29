<template>
  <div v-if="impersonated">
    <br><br>
  </div>
</template>

<script>
export default {
  data() {
    return {
      impersonated: this.$page.props.site?.impersonated,
    };
  },
};
</script>

