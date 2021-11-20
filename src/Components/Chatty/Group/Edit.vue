<template>
  <div>
    <loading-overlay :show="form.isSubmitting"></loading-overlay>

    <div class="card card-body">
      <div v-if="!itemXid">
        <div class="d-flex flex-column">
          <div class="d-flex flex-row">
            <div>
              <text-field
                v-model="form.data.name"
                :api-errors="apiErrors"
                fieldname="name"
                hint=""
                label="Name of group"
                validation-rules="required|min:2 "
              >
              </text-field>
            </div>
          </div>

          <div class="d-flex flex-row">
            <div>
              <text-field
                v-model="form.data.order"
                :api-errors="apiErrors"
                fieldname="order"
                hint="<5 = favority"
                label="Order"
                validation-rules=""
              >
              </text-field>
            </div>

            <div>
              <text-field
                v-model="form.data.icon"
                :api-errors="apiErrors"
                fieldname="icon"
                hint="favicon"
                label="Icon"
                validation-rules=""
              >
              </text-field>
            </div>
            <div>
              <text-field
                :background-color="color"
                :label="color"
                outlined
                @click="showColorPicker = !showColorPicker"
              >
              </text-field>
            </div>
          </div>
          <div class="d-flex flex-row">
            <v-color-picker
              v-if="showColorPicker"
              v-model="color"
              class="ma-2"
              dot-size="25"
              hide-inputs
              show-swatches
              swatches-max-height="200"
            ></v-color-picker>
          </div>
          <div class="d-flex flex-row justify-content-center">
            <text-area
              v-model="form.data.description"
              :api-errors="apiErrors"
              :rows="2"
              fieldname="description"
              hint="type your message"
              label="description"
              validation-rules=""
            >
            </text-area>
          </div>
        </div>
      </div>

      <div class="d-flex justify-content-end">
        <button-submit :is-loading="form.isSubmitting" class="mt-5" @click="submitGroup">
          Save Group
        </button-submit>
      </div>
    </div>
  </div>
</template>

<script>
import {ButtonSubmit} from 'bedrock-core-vue';

export default {
  components: {
    ButtonSubmit,
  },

  props: {
    group: {
      type: Object,
      required: false,
    },
  },

  created() {
    this.form.data = this.group;
    this.color = this.group.color;
  },

  data() {
    return {
      itemXid: null,
      type: 'hex',
      hex: '#FFFFFF',
      showColorPicker: false,

      form: {
        isSubmitting: false,
        data: {},
      },
      apiErrors: {},
    };
  },

  computed: {
    color: {
      get() {
        return this[this.type];
      },
      set(v) {
        this[this.type] = v;
      },
    },

    showColor() {
      if (typeof this.color === 'string') return this.color;

      return JSON.stringify(
        Object.keys(this.color).reduce((color, key) => {
          // eslint-disable-next-line no-param-reassign
          color[key] = Number(this.color[key].toFixed(2));
          return color;
        }, {}),
        null,
        2,
      );
    },
  },

  methods: {
    getSubmitUrl() {
      let url = '';
      if (!this.form.data.xid || this.form.data.xid === '0') {
        url = this.route('member.groups.store');
      } else {
        url = this.route('member.groups.update', {
          group: this.form.data.xid,
        });
      }
      return url;
    },

    submitGroup() {
      this.form.isSubmitting = true;

      this.form.data.color = this.color;
      const url = this.getSubmitUrl();

      this.clearResponses();

      this.$http
        .post(url, this.form.data)
        .then((response) => {
          const responseObject = response.data.data;
          if (responseObject.xid) {
            window.location.href = this.route('member.groups.show', responseObject.xid);
          }
        })
        .catch(() => {
          this.form.isSubmitting = false;
        })
        .finally(() => {
        });
    },

    // itemDelete() {
    //   this.form.isSubmitting = true;
    //   const url = this.route('groups.item.delete', {
    //     group_xid: this.form.data.group,
    //     item_xid: this.form.data.xid,
    //   });
    //
    //   this.$http
    //     .delete(url)
    //     .then(() => {
    //       window.location.href = this.route('member.groups.show', this.form.data.group);
    //     })
    //     .catch(() => {
    //       this.form.isSubmitting = false;
    //     });
    // },

    clearResponses() {
      //
    },
  },
};
</script>
