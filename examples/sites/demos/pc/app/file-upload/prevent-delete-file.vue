<template>
  <tiny-file-upload ref="upload" :action="action" :file-list="fileList" :before-remove="beforeRemove">
    <template #trigger>
      <tiny-button>选取文件</tiny-button>
    </template>
  </tiny-file-upload>
</template>

<script>
import { FileUpload, Button, Modal } from '@opentiny/vue'

export default {
  components: {
    TinyFileUpload: FileUpload,
    TinyButton: Button
  },
  data() {
    return {
      action: 'http://localhost:3000/api/upload',
      fileList: [
        {
          name: 'test1',
          url: `${import.meta.env.VITE_APP_BUILD_BASE_URL}static/images/fruit.jpg`
        }
      ]
    }
  },
  methods: {
    beforeRemove(file) {
      return new Promise((resolve, reject) => {
        Modal.confirm(`确定移除 ${file.name}？`).then((res) => {
          res === 'confirm' ? resolve() : reject(new Error('取消移除'))
        })
      })
    }
  }
}
</script>
