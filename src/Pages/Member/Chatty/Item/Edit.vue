<template>
  <div class="container">
    <item-edit
      :allowed-mime-types="allowedMimeTypes"
      :groups-tree="tree"
      :item="item"
      :languages="languages"
    ></item-edit>
  </div>
</template>

<script>
import ItemEdit from '../../../../Components/Chatty/Item/Edit.vue';

export default {
  components: {
    ItemEdit,
  },
  props: {
    item: Object,
    tree: Array,
    languages: Array,
    allowedMimeTypes: Array,
  },
};
</script>
