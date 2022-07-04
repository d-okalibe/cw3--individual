<script>
import { state } from "../globalState";

export default {
  data() {
    return {
      state,
    };
  },
};
</script>
<template>
  <div v-if="state.lessons.length < 1" class="row justify-content-center">
    <div class="col-sm-10">
      <p class="text-center m-0">
        <img
          style="width: 300px; object-fit: cover"
          src="assets/images/Smiley face_Two Color.svg"
          alt=""
        />
      </p>
      <p
        class="text-center m-0"
        v-if="state.search_keyword != '' && state.lessons.length < 1"
      >
        <strong>{{ state.search_keyword }}</strong> not found
      </p>
      <p class="text-center m-0" v-else>Waiting for items...</p>
    </div>
  </div>
</template>
