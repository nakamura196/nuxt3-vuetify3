<template>
  <div>
    <h1 class="mt-10 mb-10">IIIFコレクションの更新</h1>
    <p>IIIFコレクションを更新します。</p>

    <div class="mt-10 mb-10">
      <v-btn
        flat
        class="ma-2"
        rounded="pill"
        color="primary"
        @click="update"
      >
        実行
      </v-btn>
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from "axios"

definePageMeta({
  layout: "custom",
});

const update = () => {

  const url = "https://4ou4arygpk.execute-api.us-east-1.amazonaws.com/Prod/iiif"

  axios.get(url)

  alert("受け付けました。Slackを確認してください。")
}
</script>
