<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <users-overview
          :datatable-values="users"
          :filter-roles="roles"
          :title="$t('bedrock-users.admin.index.title')"
          type="ADMINS"
        ></users-overview>
      </div>
    </div>
  </div>
</template>

<script>
import {UsersOverview} from 'bedrock-users-vue';

export default {
  components: {
    UsersOverview,
  },

  props: {
    users: Array,
    roles: Array,
  },
};
</script>
