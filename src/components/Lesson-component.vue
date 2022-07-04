<script>
import { state } from "../globalState";

export default {
  data() {
    return {
      state,
    };
  },
  setup() {
    state.fetchLessons();
  },
};
</script>

<template>
  <div
    class="row"
    v-if="!state.loading && state.lessons && state.lessons.length"
  >
    <div
      class="col-sm-3 mb-2"
      v-for="activity in state.lessons"
      :key="activity._id"
    >
      <div class="card mb-3 rounded-0">
        <img
          v-bind:src="activity.url"
          class="card-img-top rounded-0 mycard-img"
        />
        <div class="card-body">
          <h6 class="card-title">{{ activity.title }}</h6>
          <p class="card-text m-0">
            <strong>Location:</strong> {{ activity.location }}
          </p>
          <p class="card-text m-0">
            <strong>Price:</strong> $ {{ activity.price }}
          </p>
          <p class="card-text mb-2">
            <strong>Spaces</strong>: {{ activity.spaces }}
            <span v-if="activity.spaces < 1" style="color: red"
              >(Out of stock)</span
            >
          </p>
          <button
            v-bind:disabled="state.disableAddToCart(activity)"
            class="btn btn-sm btn-primary rounded-0 w-100"
            v-on:click="state.addToCart(activity)"
          >
            Add to cart <i class="fas fa-cart-plus"></i>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
