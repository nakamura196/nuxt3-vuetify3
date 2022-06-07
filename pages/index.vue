<template>
  <div>
    <h1 class="mt-10 mb-10">Image API Tool</h1>
    <v-text-field
      label="Input Image API"
      variant="outlined"
      v-model="api"
      hide-details="auto"
    ></v-text-field>

    <v-btn
      flat
      class="mt-5 mb-10"
      rounded="pill"
      color="primary"
      @click="
        api =
          'https://iiif.dl.itc.u-tokyo.ac.jp/iiif/hyakki/images/hyakki.tif/29384,304,2248,1976/full/0/default.jpg'
      "
    >
      例
    </v-btn>

    <v-table>
      <thead>
        <tr>
          <th class="text-left">Field</th>
          <th class="text-left">Value</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>url</td>
          <td>
            <a target="_blank" :href="api">{{ api }}</a>
          </td>
        </tr>
        <tr>
          <td>info.json</td>
          <td>
            <a target="_blank" :href="info">{{ info }}</a>
          </td>
        </tr>
        <tr>
          <td>region</td>
          <td>{{ region }}</td>
        </tr>
        <tr>
          <td>size</td>
          <td>{{ size }}</td>
        </tr>
        <tr>
          <td>rotation</td>
          <td>{{ rotation }}</td>
        </tr>
        <tr>
          <td>quality</td>
          <td>{{ quality }}</td>
        </tr>
        <tr>
          <td>format</td>
          <td>{{ format }}</td>
        </tr>
      </tbody>
    </v-table>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  layout: "custom",
});

const api = ref<string>("");

const info = ref<string>("");
const rotation = ref<string>("");
const size = ref<string>("");
const region = ref<string>("");
const format = ref<string>("");
const quality = ref<string>("");

watch(api, (value) => {
  if (value) {
    const spl = value.split("/");
    const last = spl[spl.length - 1];

    const spl2 = last.split(".");
    format.value = spl2[1];
    quality.value = spl2[0];

    let rotation_ = spl[spl.length - 2];
    rotation.value = rotation_;

    let size_ = spl[spl.length - 3];
    size.value = size_;

    let region_ = spl[spl.length - 4];
    region.value = region_;

    info.value =
      value.split("/" + region_ + "/" + size_ + "/" + rotation_ + "/")[0] +
      "/info.json";
  }
});

/*
const format = computed(() => {
  const url = api.value;
  const spl = url.split("/");
  const last = spl[spl.length - 1];
  const ext = last.split(".")[1];
  return ext;
});
*/
</script>
