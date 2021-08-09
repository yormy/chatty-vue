<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <roles-overview :datatable-values="roles"></roles-overview>
      </div>
    </div>
  </div>
</template>

<script>
import {RolesOverview} from 'bedrock-users-vue';

export default {
  components: {
    RolesOverview,
  },
  props: {
    roles: Array,
  },
};
</script>
