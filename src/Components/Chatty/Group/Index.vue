<template>
  <div>
    <!--    <loading-overlay :show="form.isSubmitting"></loading-overlay>-->

    <div class="flex-row justify-content-center">
      <div class="d-flex justify-content-between flex-wrap groups">
        <div>
          <!--          <Link :href="route('groups.index')">-->
          <!--            <i class="fas fa-home" style="font-size: 12px"></i>-->
          <!--          </Link>-->
        </div>
        <div></div>
        <div>
          <Link :href="route('member.groups.create', { parent_xid: group.xid })">
            <i class="fas fa-plus" style="font-size: 20px">Child group</i>
          </Link>
        </div>
      </div>

      <div class="">
        <!--eslint-disable-next-line vue/no-v-html-->
        <div v-html="group.breadcrumb"></div>
        <div class="d-flex justify-content-center">
          <div v-for="child in group.children" :key="child.xid">
            <child :child="child"></child>
          </div>
        </div>
        <div class="d-flex align-content-start items">
          <h3>{{ group.name }}</h3>
          <!--          <Link :href="route('groups.edit', group.xid)">-->
          <!--            <i class="fas fa-edit" style="font-size:0.5rem"></i>&ndash;&gt;-->
          <!--          </Link>-->

          <div @click="toggleEditItems">
            Edit Items <span class="fal fa-edit"></span>
          </div>
        </div>
        <div class="d-flex align-content-start items flex-wrap">
          <div v-for="item in group.items" :key="item.xid">
            <item :editItem="editItem" :item="item"></item>
          </div>
        </div>

        <div class="item--add__floating">
          <Link :href="route('member.items.create', { group_xid: group.xid })">
            <!--            <img :src="images.app.plus_icon" height="60px"/>-->
            <img height="60px" src="/shared/images/modules/chatty/plus.png"/>
          </Link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Item from './Item.vue';
import Child from './Child.vue';

export default {
  components: {
    Item,
    Child,
  },

  props: {
    group: Object,
  },

  data() {
    return {
      images: this.$page.props.shared.images,
      editItem: false
    };
  },

  methods: {
    toggleEditItems() {
      this.editItem = !this.editItem;
    }
  }
};
</script>

<style scoped>
.item--add__floating {
  position: fixed;
  bottom: 0%;
  /*//width:100%;*/
  opacity: 1;
  right: 2rem;
}
</style>
