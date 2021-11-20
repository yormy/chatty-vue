<template>
  <div class="container">
    <Edit :group="group"></Edit>
  </div>
</template>

<script>

export default {
  components: {
    Edit,
  },
  props: {
    group: Object,
  },
};
</script>
