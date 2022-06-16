<template>
  <div class="payment-view pt-2 ps-2">
    <HeaderMart />
    <div class="container-fluid mt-3">
      <div class="row">
        <!-- 4 deret mulai -->
        <div class="col-lg border float-left">
          <div class="row-md">
            <!-- bagian alur beli -->
            <AlurMart />
          </div>
          <div class="row-md mt-4">
            <!-- payment method -->
            <div
              class="
                payment-method
                d-flex
                align-items-center
                justify-content-center
              "
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
                        <button type="button" class="btn btn-method-box" o>
                          <img src="@/assets/cc.png" alt="cc" />
                          <div style="margin-left: 10px">Credit Card</div>
                        </button>
                      </router-link>
                    </div>
                    <div class="col">
                      <router-link to="#">
                        <button type="button" class="btn btn-method-box" o>
                          <img src="@/assets/QRIS.png" alt="qris" />
                        </button>
                      </router-link>
                    </div>
                  </div>
                  <div class="row mt-me">
                    <div class="col">
                      <router-link to="#">
                        <button type="button" class="btn btn-method-box" o>
                          <img src="@/assets/gopay.png" alt="qris" />
                        </button>
                      </router-link>
                    </div>
                    <div class="col">
                      <router-link to="#">
                        <button type="button" class="btn btn-method-box" o>
                          <img src="@/assets/OVO.png" alt="qris" />
                        </button>
                      </router-link>
                    </div>
                    <div class="col">
                      <router-link to="#">
                        <button type="button" class="btn btn-method-box" o>
                          <img src="@/assets/Shopee.png" alt="qris" />
                        </button>
                      </router-link>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="row-md mt-4">
            <div class="tombol d-flex justify-content-center border">
              <div class="tombol-wrapper d-flex align-items-center">
                <div class="settings"></div>
                <div class="help"></div>
                <div class="interface-click-able">
                  <div class="back">
                    <router-link to="/scan">
                      <button type="button" class="btn-primary btn-back">
                        <img src="../../public/img/Arrow.png" alt="" />
                        <span style="margin-left: 35px"> Back </span>
                      </button>
                    </router-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- tabel bon -->
        <div class="col-lg float-left ps-5">
          <div class="bon">
            <div class="bon-header">
              <div class="d-flex align-items-end mb-3">
                <table class="" border="0">
                  <tbody>
                    <tr>
                      <td style="width: 327px">
                        <div class="row-content">
                          <h4>Nama Barang</h4>
                        </div>
                      </td>
                      <td style="width: 183px">
                        <div class="row-content">
                          <div class="text-end">
                            <h4>Harga Barang</h4>
                          </div>
                        </div>
                      </td>
                      <td style="width: 60px">&nbsp;</td>
                      <td style="width: 67px"></td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
            <div class="bon-body-payment border">
              <div
                class="bon-body-row"
                v-for="barangTable in Barang"
                v-bind:key="barangTable.id"
              >
                <table class="bon-body-row-table" border="0">
                  <tbody>
                    <tr>
                      <td style="width: 327px">
                        <div class="row-content">
                          {{ barangTable.nama }}
                        </div>
                      </td>
                      <td style="width: 183px">
                        <div class="row-content">
                          <div class="text-end">
                            {{ formatPrice(barangTable.harga) }}
                          </div>
                        </div>
                      </td>
                      <td style="width: 60px">&nbsp;</td>
                      <td style="width: 67px">
                        <button type="delete" class="btn btn-cancel">
                          <div class="cancel"></div>
                        </button>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
            <div class="bon-footer">
              <div class="bon-footer-total border">
                <table
                  style="width: 590px; height: 142px; margin-left: 22px"
                  border="0"
                >
                  <tbody>
                    <tr>
                      <td style="width: 150px" class="text-start">Sub Total</td>
                      <td class="text-end">
                        Rp {{ formatPrice(calculateSubTotal()) }}
                      </td>
                    </tr>
                    <tr>
                      <td style="width: 150px" class="text-start">PPN 11%</td>
                      <td class="text-end">
                        Rp {{formatPrice(calculatePPN(calculateSubTotal()))}}
                      </td>
                    </tr>
                    <tr
                      style="
                        font-weight: 700;
                        font-size: 48px;
                        line-height: 65px;
                      "
                    >
                      <td style="width: 150px" class="text-start">Total</td>
                      <td class="text-end">
                        Rp 
                        {{formatPrice(calculateTotal())}}
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <FooterCopyright />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderMart from "@/components/HeaderMart.vue";
import AlurMart from "@/components/AlurMart.vue";

import FooterCopyright from "@/components/FooterCopyright.vue";

import barangData from "@/assets/barang.json";

export default {
  name: "PaymentView",
  components: {
    HeaderMart,
    AlurMart,
    FooterCopyright,
  },
  data() {
    return {
      activePaymentMethod: "CashMethod",
      Barang: barangData,
    };
  },
  methods: {
    formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
    calculateSubTotal() {
      return this.Barang.map((item) => item.harga).reduce(
        (prev, curr) => prev + curr,
        0
      );
    },
    calculatePPN(value) {
      let ppn = value * (11 / 100);
      return ppn;
    },
    calculateTotal() {
      let subTotal = this.Barang.map((item) => item.harga).reduce(
        (prev, curr) => prev + curr,
        0
      );
      let total = subTotal + subTotal * (11 / 100);
      return total;
    },
  },
};
</script>

<style scoped>
body {
  background: #f4f4f4 !important;
}
.row-body {
  display: flex;

  flex-direction: column !important;
  position: absolute;
  width: 1841px;
  height: 894px;
  left: 47px;
  top: 160px;
}

.row-body .row-body-left {
  width: 100%;
}

.col {
  display: flex;
  justify-content: center;
}

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

.bon {
  width: 635px;
  height: 875px;
  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.bon-header {
  display: flex;
  /* align-items: end; */
  width: 635px;
  height: 98px;

  background: #dedede;
  border-radius: 30px 30px 0px 0px;
}

.bon-body-payment {
  height: 600px;
  overflow-x: hidden; /* Hide horizontal scrollbar */
  overflow-y: auto;
}

.bon-body-row {
  width: 635px;
  height: 42px;
  left: 0px;
  top: 0px;
  margin-top: 12px;
  background: #f4f4f4;
}

.bon-body-row-table {
  width: 614px;
  height: 42px;
}

.row-content {
  font-weight: 400;
  font-size: 24px;
  line-height: 33px;
  /* identical to box height */
  /* float:left; */

  text-align: left;

  color: #4c4c6d;
}

.cancel {
  width: 27px;
  height: 27px;

  background-image: url("@/assets/cancel.png");
}

.bon-footer-total {
  font-weight: 400;
  font-size: 28px;
  line-height: 38px;
}
</style>

<style>
.settings {
  /* position: absolute; */
  width: 79px;
  height: 70px;

  background-image: url("@/assets/settings.png");
}
.help {
  /* position: absolute; */
  width: 108px;
  height: 108px;
  margin-left: 41px;

  background-image: url("@/assets/help.png");
}
html body {
  background: #f4f4f4;
}

h2 {
  font-weight: 400 !important;
  font-size: 48px !important;
  color: #4c4c6d !important;
}
/* btn-back */
.btn-back {
  width: 272px;
  height: 100px;

  font-weight: 700;
  font-size: 40px;
  line-height: 55px;
  /* identical to box height */

  color: #4c4c6d !important;

  background: #b8e0d8;
  border-radius: 100px;
}
.btn-back:hover {
  background: #b8e0d8;
  color: black;
}

.btn-back:active {
  background: #7fa8a0;
  color: black;
  border-color: transparent;
}

.btn-back:focus {
  background: #7fa8a0;
  color: black;
  border: transparent;
  box-shadow: none;
}

.tombol-wrapper {
  width: 1139px;
  height: 108px;
  left: 0px;
  top: 49px;
}

.back {
  margin-left: 639px;
}
</style>