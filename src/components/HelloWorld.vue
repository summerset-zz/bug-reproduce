<template>
  <div class="hello">

    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>

    <div id="fullscreenContainer">
      <n-space vertical>
        <n-button @click="toggleFullscreen">切换全屏</n-button>
        <n-button @click="sendMessage('测试消息')">发消息</n-button>
      </n-space>
    </div>
  </div>
</template>

<script setup>

import { defineProps } from 'vue'

import { useMessage, NButton, NSpace } from 'naive-ui'
const message = useMessage()

function sendMessage(content) {
  message.info(content)
}

function toggleFullscreen() {
  const fullscreenContainer = document.getElementById('fullscreenContainer')
  if (!document.fullscreenElement) {
    fullscreenContainer.requestFullscreen().then(
      () => {
        // on success
        message.info('已开启全屏')
      },
      () => {
        // on fail
        message.error('全屏开启失败，您的浏览器可能不支持全屏')
      }
    )
  }
  else {
    document.exitFullscreen().then(
      () => {
        // on success
        message.info('已关闭全屏')
      },
      () => {
        // on fail
        message.error('全屏关闭失败。请使用浏览器自带的方法关闭全屏。')
      }
    )
  }
}



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
