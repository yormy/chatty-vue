<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <settings :settings="allSettings"></settings>
      </div>
    </div>
  </div>
</template>

<script>
import Settings from '../../../../../Components/Settings/Settings';

export default {
  components: {
    Settings,
  },

  props: {
    allSettings: Object,
  },
};
</script>
