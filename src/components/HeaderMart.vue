<template>
  <!-- Header Section Begin -->
  <header class="header-section">
    <div class="container">
      <div class="inner-header">
        <div class="row">
          <div class="col-lg-3 float-left">
            <div class="logo">
              <img src="@/assets/Logo-text.png" alt="Logo" />
            </div>
            <div class="empty"></div>
          </div>
        </div>
      </div>
    </div>
  </header>
  <!-- Header End -->
</template>

<script>
export default {
  name: "HeaderMart",
};
</script>

<style scoped>
.empty {
  width: 1489px;
}
.header-section {
  height: 100px;
  width: 100%;
}

.logo {
  position: absolute;
  height: 77px;
  left: 50px;
  /* top: 50px; */
}

.photo-item {
  width: 80px;
  height: 80px;
}
</style>