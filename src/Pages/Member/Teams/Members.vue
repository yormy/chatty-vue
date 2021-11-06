<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        {{ members }}==
        <team-members-index
          :invites="invites"
          :members="members"
          :team="team"
          :title="$t('bedrock-users.admin.index.title')"
        ></team-members-index>
      </div>
    </div>
  </div>
</template>

<script>
import {TeamMembersIndex} from 'bedrock-users-vue';

export default {
  components: {
    TeamMembersIndex,
  },

  props: {
    team: {
      type: Object,
      required: true
    },

    members: {
      type: Array,
      required: true
    },

    invites: {
      type: Array,
      required: true
    },

  },
};
</script>
