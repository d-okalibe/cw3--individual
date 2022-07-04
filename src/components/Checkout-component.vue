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
  <div
    class="modal fade"
    id="cartModal"
    tabindex="-1"
    aria-labelledby="cartModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-lg modal-dialog-scrollable">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">
            My cart <i class="fas fa-shopping-cart"></i>
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="row">
            <div class="col-sm-7">
              <!-- Cart items -->
              <div class="row">
                <h6>Cart Items</h6>
                <!-- No items in the cart error message -->
                <div
                  v-if="state.countCart() < 1"
                  class="row justify-content-center"
                >
                  <div class="col-sm-10">
                    <p class="text-center m-0">
                      <img
                        style="width: 200px; object-fit: cover"
                        src="assets/images/Smiley face_Two Color.svg"
                        alt=""
                      />
                    </p>
                    <p class="text-center m-0">No items in the cart</p>
                  </div>
                </div>
                <!-- Loop through cart items -->
                <div
                  class="col-sm-6"
                  v-for="item in state.cartItemsInfo()"
                  :key="item.id"
                >
                  <div class="card mb-3 rounded-0">
                    <img
                      :src="item.url"
                      class="card-img-top rounded-0 mycard-img"
                      :alt="item.title"
                    />
                    <div class="card-body">
                      <h6 class="card-title">{{ item.title }}</h6>
                      <p class="card-text m-0">
                        <strong>Location:</strong> {{ item.location }}
                      </p>
                      <p class="card-text m-0">
                        <strong>Price:</strong> $ {{ item.price }}
                      </p>
                      <p class="card-text m-0">
                        <strong>Spaces:</strong> {{ item.spaces }}
                      </p>
                      <button
                        v-on:click="state.removeFromCart(item.id, item.spaces)"
                        class="btn mt-1 btn-sm btn-danger rounded-0 w-100"
                      >
                        Remove from cart <i class="fas fa-cart-arrow-down"></i>
                      </button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <!-- Check out form -->
            <div class="col-sm-5">
              <h5>Checkout <i class="fas fa-paper-plane"></i></h5>
              <div class="total-price">
                <div class="d-flex">
                  <p class="m-0"><strong>Total:</strong></p>
                  <p class="ms-auto">$ {{ state.totalPrice() }}</p>
                </div>
              </div>
              <div class="row mb-2">
                <div class="col">
                  <input
                    v-model="state.order_details.firstname"
                    type="text"
                    class="form-control rounded-0"
                    placeholder="First name"
                    aria-label="First name"
                  />
                </div>
                <div class="col">
                  <input
                    v-model="state.order_details.lastname"
                    type="text"
                    class="form-control rounded-0"
                    placeholder="Last name"
                    aria-label="Last name"
                  />
                </div>
              </div>
              <input
                type="text"
                v-model="state.order_details.mobile"
                class="form-control rounded-0 mb-2"
                placeholder="Phone number"
                aria-label="Last name"
              />
              <button
                v-bind:disabled="state.validateFields()"
                v-on:click="state.checkOut()"
                class="btn btn-success w-100 rounded-0"
              >
                Checkout <i class="fas fa-paper-plane"></i>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
