<template>
  <aside>
    <h2 class="mb-6 text-2xl md:text-3xl">
      {{ $t('image-details.related-images') }}
    </h2>
    <VLoadingIcon v-if="fetchState.isFetching" />
    <VImageGrid
      :images="media"
      :show-load-more="false"
      :fetch-state="fetchState"
    />
  </aside>
</template>

<script lang="ts">
import { defineComponent, PropType } from '@nuxtjs/composition-api'

import type { ImageDetail } from '~/models/media'
import type { FetchState } from '~/models/fetch-state'

import VImageGrid from '~/components/VImageGrid/VImageGrid.vue'
import VLoadingIcon from '~/components/LoadingIcon.vue'

export default defineComponent({
  name: 'VRelatedImages',
  components: { VImageGrid, VLoadingIcon },
  props: {
    media: {
      type: Array as PropType<ImageDetail[]>,
      required: true,
    },
    fetchState: {
      type: Object as PropType<FetchState>,
      required: true,
    },
  },
})
</script>
