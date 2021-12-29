<template>
  <div>
    <div class="footer">
      {{ branding.copyright }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      branding: this.$page.props.site.branding,
    };
  },
};
</script>
