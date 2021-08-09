<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <users-overview
          :datatable-values="users"
          :filter-memberships="memberships"
          :filter-roles="roles"
          :impersonate-user-allowed="impersonateAllowed"
          :title="$t('bedrock-users.member.index.title')"
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
    memberships: Array,
    impersonateAllowed: Boolean,
  },
};
</script>
