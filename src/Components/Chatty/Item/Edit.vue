<template>
  <div>
    <loading-overlay :show="form.isSubmitting"></loading-overlay>
    <!--    :label="$t('bedrock-users.login.loginname.label')"-->
    <!--    :hint="$t('bedrock-users.login.loginname.hint')"-->

    <chip> 88888</chip>

    <ValidationObserver ref="form">
      <div class="card card-body">
        <div v-if="!itemXid">
          <div class="d-flex flex-column">
            <div class="d-flex flex-row">
              <div>
                <text-field
                  v-model="form.data.title"
                  :api-errors="apiErrors"
                  fieldname="title"
                  hint=""
                  label="Internal Title"
                  validation-rules=""
                >
                </text-field>
              </div>
            </div>
            <div class="row">
              <div class="col-md-2">
                <dropdown v-model="form.data.group" :items="groupsTree" label="Group"></dropdown>
              </div>

              <div class="col-md-2">
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

              <div class="col-md-2">
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

              <div class="col-md-2">
                <text-field
                  :background-color="color"
                  :label="color"
                  @click="showColorPicker = !showColorPicker"
                >
                </text-field>
              </div>

              <div class="col-md-2">
                <dropdown
                  v-model="form.data.language"
                  :api-errors="apiErrors"
                  :items="languages"
                  fieldname="language"
                  label="language"
                ></dropdown>
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
            <div class="d-flex flex-row w-100">
              <text-area
                v-model="form.data.text"
                :api-errors="apiErrors"
                :rows="6"
                fieldname="text"
                hint="type your message"
                label="Text"
                validation-rules=""
              >
              </text-area>
            </div>
          </div>
        </div>

        <div v-if="form.data.has_media">
          <div class="d-flex flex-row justify-content-center">
            <div class="d-flex flex-column">
              <div>
                <img
                  v-if="form.data.is_image"
                  :src="form.data.preview_url"
                  alt="Image"
                  class="item--image"
                  style="max-height: 200px; max-width: 200px"
                />

                <video v-if="form.data.is_video" controls="controls" width="320">
                  <source :src="item.file_url" type="video/mp4"/>
                </video>

                <div v-if="form.data.is_pdf">
                  <embed :src="item.file_url" width="130px"/>
                  <span class="fal fa-eye" @click="openPdf(item.file_url)"></span>
                </div>

                <div v-if="form.data.is_document">
                  DOCUMENT:
                  <a :href="item.file_url">CLICK TO OPEN</a>
                </div>
              </div>

              <div class="text-center">
                <button-submit
                  :is-loading="form.isSubmitting"
                  btn-class="mt-2 btn btn-danger"
                  @click="deleteImage"
                >
                  <span class="fal fa-trash">&nbsp;</span>
                </button-submit>
              </div>
            </div>
          </div>
        </div>

        <div v-if="!form.data.has_media">
          <div class="d-flex flex-column">
            <h4>Upload file (optional)</h4>
            <file-dropzone-upload
              :additional-data="additionalUploadData"
              :allowed-mime-types="allowedMimeTypes"
              :associated-xid="form.data.xid"
              upload-route="member.items.upload"
              @fileAdded="form.isSubmitting = true"
              @uploadError="form.isSubmitting = false"
              @uploadSuccess="uploadSuccess"
            >
            </file-dropzone-upload>
          </div>
        </div>

        <div class="d-flex justify-content-between">
          <button-submit
            :is-loading="form.isSubmitting"
            btn-class="mt-5 btn btn-danger"
            @click="itemDelete"
          >
            Delete Item
          </button-submit>

          <button-submit :is-loading="form.isSubmitting" class="mt-5" @click="submitItem">
            Save Item
          </button-submit>
        </div>
      </div>
    </ValidationObserver>
  </div>
</template>

<script>
import {ButtonSubmit} from 'bedrock-core-vue';

export default {
  components: {
    ButtonSubmit,
  },

  props: {
    groupsTree: {
      type: Array,
      required: false,
    },

    languages: {
      type: Array,
      required: false,
    },

    allowedMimeTypes: {
      type: Array,
      required: false,
    },

    item: {
      type: Object,
      required: false,
    },

    filepath: {
      type: String,
      required: false,
    },
  },

  created() {
    this.form.data = this.item;
    this.color = this.item.color;
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

    additionalUploadData() {
      const additionalData = {
        group_xid: this.form.data.group,
        item: this.form.data,
      };
      return JSON.stringify(additionalData);
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
    openPdf(url) {
      window.open(url);
    },

    uploadSuccess(response) {
      const selectedGroup = this.form.data.group;
      this.form.data = response.data;
      this.form.data.group = selectedGroup;

      this.form.isSubmitting = false;
    },

    deleteImage() {
      const url = this.route('member.items.image.destroy', {
        item: this.form.data.xid,
      });

      const self = this;
      this.$http
        .delete(url)
        .then(() => {
          self.form.data.has_media = false;
          self.form.data.preview_url = null;
          self.form.data.thumbnail_url = null;
          self.form.data.filename_original = null;
        })
        .catch(() => {
        });
    },

    getSubmitUrl() {
      let url = '';
      if (!this.form.data.xid || this.form.data.xid === '0') {
        url = this.route('member.items.store');
      } else {
        url = this.route('member.items.update', {
          item: this.form.data.xid,
        });
      }
      return url;
    },

    submitItem() {
      this.form.isSubmitting = true;

      this.form.data.color = this.color;
      const url = this.getSubmitUrl();

      this.clearResponses();

      this.$http
        .post(url, this.form.data)
        .then((response) => {
          const responseObject = response.data.data;
          if (responseObject.xid) {
            // this.itemXid = response.data.xid;

            const selectedGroup = this.form.data.group;
            this.form.data = responseObject;
            this.form.data.group = selectedGroup;
            window.location.href = this.route('member.groups.show', this.form.data.group);
          }
        })
        .catch((error) => {
          this.form.isSubmitting = false;
          this.apiErrors = error.response.data;
        })
        .finally(() => {
        });
    },

    itemDelete() {
      this.form.isSubmitting = true;
      const url = this.route('member.items.destroy', {
        group_xid: this.form.data.group,
        item: this.form.data.xid,
      });

      this.$http
        .delete(url)
        .then(() => {
          window.location.href = this.route('member.groups.show', this.form.data.group);
        })
        .catch(() => {
          this.form.isSubmitting = false;
        });
    },

    clearResponses() {
      //
    },
  },
};
</script>
