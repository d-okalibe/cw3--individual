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
  <nav class="navbar navbar-light bg-white border-bottom navbar-expand">
    <div class="container-fluid">
      <a class="navbar-brand fw-bold" href="#">🦸SchoolHero</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <button
              v-bind:disabled="state.hideCart()"
              type="button"
              class="btn rounded-0 btn-sm btn-dark position-relative"
              data-bs-toggle="modal"
              data-bs-target="#cartModal"
            >
              <i class="fas fa-shopping-cart"></i>
              <span
                class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger"
              >
                {{ state.countCart() }}
              </span>
            </button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
