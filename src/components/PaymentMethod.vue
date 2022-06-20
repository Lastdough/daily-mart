<template>
  <div class="row mt-5">
    <!-- payment method -->
    <div
      class="payment-method d-flex align-items-center justify-content-center"
    >
      <div class="method-wrapper border">
        <div class="title-method border">
          <h3>Metode Pembayaran</h3>
        </div>
        <div class="method justify-content-center border">
          <div class="row">
            <div class="col">
              <router-link to="#">
                <button type="button" class="btn btn-method-box">
                  <img src="@/assets/Cash.png" alt="cash" />
                  <div style="margin-left: 64px">Cash</div>
                </button>
              </router-link>
            </div>
            <div class="col">
              <router-link to="#">
                <button type="button" class="btn btn-method-box" disabled>
                  <img src="@/assets/cc.png" alt="cc" />
                  <div style="margin-left: 10px">Credit Card</div>
                </button>
              </router-link>
            </div>
            <div class="col">
              <router-link to="#">
                <button type="button" class="btn btn-method-box" disabled>
                  <img src="@/assets/QRIS.png" alt="qris" />
                </button>
              </router-link>
            </div>
          </div>
          <div class="row mt-me">
            <div class="col">
              <router-link to="#">
                <button type="button" class="btn btn-method-box" disabled>
                  <img src="@/assets/gopay.png" alt="qris" />
                </button>
              </router-link>
            </div>
            <div class="col">
              <router-link to="#">
                <button type="button" class="btn btn-method-box" disabled>
                  <img src="@/assets/OVO.png" alt="qris" />
                </button>
              </router-link>
            </div>
            <div class="col">
              <router-link to="#">
                <button type="button" class="btn btn-method-box" disabled>
                  <img src="@/assets/Shopee.png" alt="qris" />
                </button>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "PaymentMethod",
};
</script>


<style scoped>
.payment-method {
  width: 1157px;
  height: 431px;

  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.method-wrapper {
  /*  */
  width: 100%;
  padding-left: 40px;
  padding-right: 40px;
}

.title-method {
  height: 41px;
  margin-top: 21px;
}

.method {
  /* position: absolute; */
  width: 1078px;
  height: 339px;
  margin-top: 22px;
}

.btn-method-box {
  display: flex;
  align-items: center;
  padding: 20px;

  box-sizing: border-box;
  width: 326px;
  height: 124px;
  left: 0px;
  top: 0px;
  /* background: #FFFFFF; */
  border: 4px solid #cccccc;
  border-radius: 20px;

  /* text */
  font-weight: 700;
  font-size: 30px;
  line-height: 41px;

  /* identical to box height */

  text-align: center;

  color: #4c4c6d;
}

.mt-me {
  margin-top: 69px !important;
}
</style>