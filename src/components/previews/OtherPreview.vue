<script setup lang="ts">
import { download } from '~/utils/ButtonUtil'

const fileInfo = defineProps(['value'])
const { text, copy, copied, isSupported } = useClipboard(fileInfo.value.url)
const { t } = useI18n()

const handleDownload = (url: string) => {
  download(url)
}
</script>

<template>
  <a-alert type="warning">看起来没有针对当前文件格式的预览呢，不过您也可以直接下载！</a-alert>
  <a-divider orientation="left">{{ t('table.Optional') }}</a-divider>
  <a-space wrap>
    <button type="button" @click='handleDownload(fileInfo.value.url)' class="inline-block px-6 py-2 border-2 border-blue-600 text-blue-600 font-medium text-xs leading-tight uppercase rounded hover:bg-black hover:bg-opacity-5 focus:outline-none focus:ring-0 transition duration-150 ease-in-out">
      <icon-download /> {{ t('button.download') }}
    </button>
    <button type="button" @click='copy(fileInfo.value.url)' class="inline-block px-6 py-2 border-2 border-blue-400 text-blue-400 font-medium text-xs leading-tight uppercase rounded hover:bg-black hover:bg-opacity-5 focus:outline-none focus:ring-0 transition duration-150 ease-in-out">
      <icon-copy /> {{ !copied ? t('button.copyUrl') : t('button.copyOk') }}
    </button>
    <button type="button" class="cursor-not-allowed inline-block px-6 py-2 border-2 border-gray-200 text-gray-200 font-medium text-xs leading-tight uppercase rounded hover:bg-black hover:bg-opacity-5 focus:outline-none focus:ring-0 transition duration-150 ease-in-out">
      其它操作开发中
    </button>
  </a-space>
</template>

<style scoped>

</style>
