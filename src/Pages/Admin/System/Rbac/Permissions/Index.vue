<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <permissions-overview
          :datatable-values="permissions"
          :filter-guards="guards"
          :filter-roles="roles"
        >
        </permissions-overview>
      </div>
    </div>
  </div>
</template>

<script>
import {PermissionsOverview} from 'bedrock-users-vue';

export default {
  components: {
    PermissionsOverview,
  },

  props: {
    permissions: Array,
    roles: Array,
    guards: Array,
  },
};
</script>
