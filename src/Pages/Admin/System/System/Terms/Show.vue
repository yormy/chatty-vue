<template>
  <div class="container mw-100">
    <div class="card">
      <div class="card-body">
        <div class="d-flex float-right">
          <locale-switcher></locale-switcher>
        </div>
        <h1>{{ title }}</h1>
        <h3>{{ subtitle }}</h3>
        <!--eslint-disable-next-line vue/no-v-html-->
        <div v-html="htmlContent"></div>
      </div>
    </div>
  </div>
</template>

<script>
import {LocaleSwitcher} from 'bedrock-core-vue';

export default {
  components: {
    LocaleSwitcher,
  },

  props: {
    title: String,
    subtitle: String,
    htmlContent: String,
  },
};
</script>
