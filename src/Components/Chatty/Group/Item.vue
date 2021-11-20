<template>
  <div>
    <div :class="item.has_media ? '' : 'w-100'" class="card my-2 mx-2">
      <div class="card-header">
        <!--           @if($item->color)-->
        <!--        style="background-color:{{$item->color}}"-->
        <!--        @endif-->
        <div>
          <i v-if="item.icon" :class="item.icon" style="font-size: 24px"></i>
        </div>

        <div>
          <strong>{{ item.title }}</strong>
          <Link v-if="editItem" :href="route('member.items.edit', item.xid)"><i
            class="fas fa-edit"></i></Link>
        </div>
      </div>
      <div class="card-body">
        <!--        @if($item->color)-->
        <!--        style="background-color:{{$item->color}}"-->
        <!--        @endif>-->
        <div
          :data-sharable-text="item.text"
          class="item--copy--trigger display-text"
          @click="share(item.text)"
        >
          {{ item.text }}
          <!--      nl2br-->
        </div>
        <div v-if="item.thumbnail_url || item.file_url">
          <div class="d-flex flex-column">
            <div>
              <div v-if="item.is_image">
                <img :src="item.file_url" alt="Image" class="item--image"/>
              </div>

              <div v-if="item.is_video">
                <video controls="controls" width="200">
                  <source :src="item.file_url" type="video/mp4"/>
                </video>
              </div>
            </div>

            <div v-if="item.is_animated">
              <div class="item--notification"><B>Download</B> before sharing</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: Object,
    editItem: {
      Type: Boolean
    }
  },

  methods: {
    share(text) {
      this.copy(text);

      if ('share' in navigator) {
        navigator.share({
          // title: document.title,
          text,
          // url: location.href,
        });
      } else {
        // Here we use the WhatsApp API as fallback; remember to encode your text for URI
        // location.href = 'https://api.whatsapp.com/send?text=' + encodeURIComponent(text + ' - ') + location.href // same window

        window.open(
          `https://api.whatsapp.com/send?text=${encodeURIComponent(`${text} - `)}${location.href}`, // eslint-disable-line
          '_blank', // <- Theis is what makes it open in a new window.
        );
      }
    },

    copy(text) {
      navigator.clipboard.writeText(text).then(
        () => {
          /* clipboard successfully set */
        },
        () => {
          /* clipboard write failed */
        },
      );
      this.$toast('Copied to clipboard');
    },
  },
};
</script>
<style scoped>
.card .card-body {
  padding-top: 1px;
  padding-bottom: 1px;
  padding-left: 1px;
  padding-right: 1px;
}

.card .card-header {
  padding-top: 1px;
  padding-bottom: 1px;
  padding-left: 1px;
  padding-right: 1px;
}

.item--image {
  max-height: 100px;
  max-width: 100px;
}

.item--notification {
  font-size: 0.5rem;
}
</style>
