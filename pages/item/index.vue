<template>
  <div>
    <h1 class="mt-10 mb-10">アイテム更新</h1>
    <p>単一のアイテムを更新します。</p>

    <v-text-field
      class="mt-10"
      label="URI"
      placeholder="https://ld.cultural.jp/data/iiifman-dgcl-doshisha-ac_50000_MD00000001"
      variant="outlined"
      v-model="uri"
      hide-details="auto"
    ></v-text-field>

    <v-select
      class="mt-10"
      :items="items"
      label="Endpoint"
      v-model="endpoint"
      variant="outlined"
      hide-details="auto"
    ></v-select>

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

      <v-btn
        flat
        class="ma-2"
        rounded="pill"
        color="info"
        @click="uri = 'https://ld.cultural.jp/data/iiifman-dgcl-doshisha-ac_50000_MD00000001'"
      >
      例
      </v-btn>
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from "axios"

definePageMeta({
  layout: "custom",
});

const uri = ref<string>("");

const endpoint = ref<string>("Cultural Japan");

const items = ref<any>([
  "Japan Search",
  "Cultural Japan"
]);

const update = async () => {
  const uri_ = uri.value
  const endpoint_ = endpoint.value
  //console.log("uri", uri_, "endpoint", endpoint_)

  const url = "https://4ou4arygpk.execute-api.us-east-1.amazonaws.com/Prod/hello"

  axios.get(url, {
    params: {
      uri: uri_,
      endpoint: endpoint_
    }
  })

  // const {data} = await 
  // console.log({data})
}
</script>
