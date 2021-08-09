<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <term-edit :model="term"></term-edit>
      </div>
    </div>
  </div>
</template>

<script>
import {TermEdit} from 'bedrock-users-vue';

export default {
  components: {
    TermEdit,
  },
  props: {
    term: Object,
  },
};
</script>
