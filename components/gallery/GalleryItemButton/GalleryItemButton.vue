<template>
  <div class="buttons is-align-content-start gallery-button">
    <GalleryItemShareBtn data-testid="gallery-item-share-button" />
    <GalleryItemMoreActionBtn
      :ipfs-image="nftMetadata?.image"
      :mime-type="nftMimeType"
      :name="nft?.name"
      :current-owner="nft?.currentOwner"
      :price="nft?.price"
      data-testid="gallery-item-more-button" />
  </div>
</template>

<script setup lang="ts">
import GalleryItemShareBtn from './GalleryItemShareBtn.vue'
import GalleryItemMoreActionBtn from './GalleryItemMoreActionBtn.vue'
import { GalleryItem } from '../useGalleryItem'

const props = defineProps<{
  galleryItem: GalleryItem
}>()

const nft = computed(() => props.galleryItem.nft.value)
const nftMimeType = computed(() => props.galleryItem.nftMimeType.value)
const nftMetadata = computed(() => props.galleryItem.nftMetadata.value)
</script>

<style scoped lang="scss">
@import '@/assets/styles/abstracts/variables';

.gallery-button {
  display: flex;
  gap: 1rem;

  @include mobile {
    flex-direction: column-reverse;
  }
}
</style>
