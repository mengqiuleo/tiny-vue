<template>
  <tiny-file-upload :action="action" :limit="limit" @exceed="handleExceed" multiple is-hidden>
    <tiny-button> 点击上传 </tiny-button>
  </tiny-file-upload>
</template>

<script setup>
import { ref } from 'vue'
import { FileUpload as TinyFileUpload, Button as TinyButton, Modal } from '@opentiny/vue'

const action = ref('http://localhost:3000/api/upload')
const limit = ref(1)

function handleExceed() {
  Modal.message(`文件个数不能超过${limit.value}个`)
}
</script>
