<template functional>
  <b-media no-body>
    <b-media-aside vertical-align="center">
      <b-img-lazy
        v-if="props.album.image"
        :src="props.album.image.url"
        :alt="`${props.album.name}'s album art`"
        height="200"
        width="200"
      />
      <b-img-lazy
        v-else
        alt="Default album art"
        height="200"
        width="200"
        src="~/assets/empty-artist-picture.png"
      />
    </b-media-aside>

    <b-media-body class="ml-4">
      <p class="font-weight-bold d-block">
        {{ props.album.name }}
      </p>
      <spotify-button
        :spotify-uri="`https://open.spotify.com/album/${props.album._id}`"
      />
    </b-media-body>
  </b-media>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue';
import SpotifyButton from '@/components/SpotifyButton.vue';
import Album from '@/types/Album';

Vue.component('spotify-button', SpotifyButton);

export default Vue.extend({
  name: 'AlbumPreview',
  props: {
    album: {
      type: Object as PropType<Album>,
      required: true
    }
  }
});
</script>
