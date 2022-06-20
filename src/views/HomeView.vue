<template>
  <div class="home">
    <div class="row-header">
      <header class="header-section">
        <div class="container">
          <div class="inner-header">
            <div class="row">
              <div class="col-lg-3 float-left">
                <div class="logo">
                  <a href="./index.html">
                    <img src="../assets/Logo.png" alt="Logo" />
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </header>
    </div>
    <div class="row carrousel">
      <CarrouselHome />
    </div>
    <div class="row footer">
      <div class="container mt-4">
        <div class="wrapper d-flex justify-content-center">
          <router-link to="/main">
            <button
              type="button"
              class="btn btn-primary btn-lg align-items-center btn-home-footer"
            >
              Next
            </button>
          </router-link>
        </div>
      </div>
    </div>
    <div class="copyright">
      <FooterCopyright />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import CarrouselHome from "@/components/CarrouselHome.vue";
import FooterCopyright from "@/components/FooterCopyright.vue";

export default {
  components: {
    CarrouselHome,
    FooterCopyright,
  },
};
</script>

<style scoped>

.header-section {
  /* background: blue; */
  width: 100%;
  height: 200px;
}
.logo {
  position: absolute;
  width: 33%;
  left: 50px;
  top: 50px;
  /* top: 25%; */
  /* bottom: 25%; */
}

.btn-home-footer {
  width: 400px;
  height: 100px;
  background: #b8e0d8;
  border-radius: 100px;
  border: transparent;

  /* text */
  font-weight: 400;
  font-size: 40px;
  line-height: 55px;
  /* identical to box height */

  color: #000000;
}

.btn-home-footer:hover {
  background: #b8e0d8;
  color: black;
}

.btn-home-footer:active {
  background: #7fa8a0;
  color: black;
  border-color: transparent;
}

.btn-home-footer:focus {
  background: #7fa8a0;
  color: black;
  border: transparent;
  box-shadow: none;
}
</style>

<style>
.home {
  overflow-x: hidden;
  width: 100%;
}

</style>
