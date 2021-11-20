<template>
  <div>
    <Link :href="route('member.groups.show', child.xid)">
      <div class="flex-row mx-2 category">
        <!-- @if($child->
       color)-->
        <!--        style="background-color:{{$child->color}}"-->
        <!--        @endif-->

        <div class="d-flex justify-content-center category--logo">
          <div v-if="child.filename">
            <!--  <img class="category&#45;&#45;logo" src="{{asset($child->filename)}}"/>-->
          </div>

          <div v-else>
            <i class="child.icon" style="font-size: 24px"></i>
          </div>
        </div>
        <div class="d-flex justify-content-center">
          <div class="d-flex justify-content-center category--title">
            <div class="btn btn-link">{{ child.name }}</div>
          </div>
        </div>
      </div>
    </Link>
  </div>
</template>

<script>
export default {
  components: {},

  props: {
    child: Object,
  },
};
</script>
