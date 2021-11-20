<template>
  <div class="flex-row justify-content-center">
    <div class="d-flex justify-content-between flex-wrap groups"></div>

    <div class="">
      <index :group="group"></index>
      <!--        <div>{!! group->breadcrumb() !!}</div>-->
      <!--        <div class="d-flex justify-content-center">-->
      <!--          @foreach ($group->children as $child)
      @include('chatty.groups.partials._show') @endforeach-->
      <!--        </div>-->
      <!--        <div class="d-flex align-content-start items">-->
      <!--          <h3>{{$group->name}}</h3>-->

      <!--          <a href="{{ route('groups.edit', ['group' => $group]) }}">-->
      <!--            <i class="fas fa-edit" style="font-size: 0.5rem"></i>-->
      <!--          </a>-->
      <!--        </div>-->

      <!--        <div class="d-flex align-content-start items flex-wrap">-->
      <!--          @foreach ($group->items as $item)
      @include('chatty.items.partials._show') @endforeach-->
      <!--        </div>-->
    </div>
  </div>
</template>

<script>
import Index from '../../../../Components/Chatty/Group/Index.vue';

export default {
  components: {
    Index,
  },
  props: {
    group: Object,
  },
};
</script>
