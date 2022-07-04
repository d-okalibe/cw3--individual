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
  <!-- Page-caption and filters-->
  <div class="container-fluid border-bottom mt-3">
    <div class="row justify-content-center">
      <div class="col-md-7">
        <h1 class="text-center page-caption">
          2,500+ after-school activities to power up your learning.
        </h1>
        <p class="text-center">
          Discover new after-school activities and classes that will help shape
          your mind, body and your future 🚀!
        </p>
      </div>
    </div>
    <div class="container">
      <div class="row mb-3 mt-2 justify-content-center">
        <div class="col-md-12">
          <div class="row justify-content-center">
            <div class="col-sm-5 mb-2">
              <input
                v-on:input="state.filterLessons"
                v-model="state.search_keyword"
                type="text"
                class="form-control rounded-0 p-2"
                placeholder="Search names, locations for interesting activities..."
                aria-label="Recipient's username"
                aria-describedby="button-addon2"
              />
            </div>
            <div class="col-sm-4 mb-2">
              <select
                v-on:change="state.sortList"
                v-model="state.attribute_sort"
                class="form-select p-2 rounded-0"
              >
                <option value="">-- Sort options --</option>
                <option value="title">Subject</option>
                <option value="location">Location</option>
                <option value="price">Price</option>
                <option value="spaces">Availability</option>
              </select>
            </div>
            <div class="col-sm-3 mb-2">
              <select
                v-on:change="state.sortList"
                v-model="state.sort_order"
                class="form-select p-2 rounded-0"
              >
                <option value="">-- Sort order --</option>
                <option value="ascending">Ascending</option>
                <option value="descending">Descending</option>
              </select>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
