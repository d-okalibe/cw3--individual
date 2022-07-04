<!-- //Root component -->
<script>
import NavbarComponent from "./components/Navbar-component.vue";
import PagecationComponent from "./components/Pagecation-component.vue";
import NoResultsErrotrComponent from "./components/NoResultsError-component.vue";
import LessonComponent from "./components/Lesson-Component.vue";
import FooterComponent from "./components/Footer-component.vue";
import CheckoutComponent from "./components/Checkout-component.vue";
export default {
  components: {
    NavbarComponent,
    PagecationComponent,
    NoResultsErrotrComponent,
    LessonComponent,
    CheckoutComponent,
    FooterComponent,
  },
};
</script>

<template>
  <main>
    <NavbarComponent />
    <div class="container mt-4">
      <PagecationComponent />
      <LessonComponent />
      <CheckoutComponent />
      <NoResultsErrotrComponent />
    </div>
    <FooterComponent />
  </main>
</template>

<style></style>
