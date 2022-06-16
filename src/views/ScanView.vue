<template>
  <div class="scan-view pt-2 ps-2">
    <HeaderMart />
    <div class="container-fluid mt-3">
      <div class="row">
        <!-- 4 deret mulai -->
        <div class="col-lg float-left">
          <div class="row-md">
            <!-- bagian alur beli -->
            <AlurMart />
          </div>
          <div class="row-md mt-4">
            <!-- bagian item text pas di scan -->
            <div class="scannedItem">
              <table class="scannedItemTable">
                <tbody>
                  <tr>
                    <!-- <td style="width: 742px"> -->
                    <td>
                      <span class="text-start">
                        <h2>
                          {{ namaBarangScanned }}
                        </h2>
                      </span>
                    </td>
                    <!-- <td style="width: 252px">&nbsp;</td> -->
                    <!-- <td style="width: 356px"> -->
                    <td>
                      <!-- <h2>{{ hargaBarang }}</h2> -->
                      <span class="text-end">
                        <h2>
                          {{ hargaBarangScanned }}
                        </h2>
                      </span>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
          <div class="row-md mt-4">
            <!-- static -->
            <div class="pesan-box">
              <div class="container d-flex">
                <div class="cola float-left"></div>
                <div class="botol"></div>
                <div class="barcode"></div>
                <div class="pesan">Scan Barcode Barang</div>
              </div>
            </div>
          </div>
          <div class="row-md mt-4">
            <div class="tombol d-flex justify-content-center">
              <div class="tombol-wrapper d-flex align-items-center">
                <div class="settings"></div>
                <div class="help"></div>
                <div class="interface-click-able"></div>
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
            <div class="bon-body">
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
              <div class="bon-footer-total">
                <table
                  style="width: 536px; height: 123px; margin-left: 48px"
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
                      <td class="text-end">Rp {{formatPrice(calculatePPN(calculateSubTotal()))}}</td>
                    </tr>
                    <tr>
                      <td style="width: 150px" class="text-start">Total</td>
                      <td class="text-end">Rp 
                        {{formatPrice(calculateTotal())}}
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <div class="bon-footer-checkout mt-4">
                <router-link to="/payment">
                  <button
                    type="button"
                    class="btn btn-primary btn-checkout btn-lg"
                  >
                    Checkout
                  </button>
                </router-link>
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
// import BonMart from "@/components/BonMart.vue";
import FooterCopyright from "@/components/FooterCopyright.vue";

import barangData from "@/assets/barang.json";

export default {
  name: "ScanView",
  components: {
    HeaderMart,
    AlurMart,
    // BonMart,
    FooterCopyright,
  },
  data() {
    return {
      subTotal: '',
      Total: 0,

      Barang: barangData,
      namaBarangScanned: "Adem Sari Ching Ku 320 mL",
      hargaBarangScanned: "Rp 7.000",
    };
  },
  methods: {
    formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
    calculateSubTotal() {
      return this.Barang.map(item => item.harga).reduce((prev, curr) => prev + curr, 0);
    },
    calculatePPN(value){
      let ppn = value*(11/100)
      return ppn
    },
    calculateTotal(){
      let subTotal =this.Barang.map(item => item.harga).reduce((prev, curr) => prev + curr, 0);
      let total = subTotal + (subTotal*(11/100))
      return total
    }
  },
};
</script>

<style scoped>
.scanBarcode {
  background-image: url("@/assets/scanBarcodeG.png") !important;
}

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

.scan-view {
  height: 100%;
  width: 100%;
}

.scannedItem {
  display: flex;
  align-items: center;

  width: 1157px;
  height: 142px;
  /* left: 0px;
  top: 0px; */

  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.scannedItemTable {
  width: 1098px;
  height: 79px;
  margin-left: 43px;
  margin-right: 43px;
}

.pesan-box {
  display: flex;

  flex-direction: column;

  width: 1157px;
  height: 218px;

  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.wrapper-pesan {
  position: absolute;
  width: 1157px;
  height: 218px;
  left: 0px;
  top: 474px;
}

.cola {
  width: 61px;
  height: 99px;
  margin-top: 112px;
  margin-bottom: 7px;
  margin-right: 22px;
  margin-left: 30px;
  /* margin: 112px 22px 7px 51px; */
  /* top | right | bottom | left */

  background-image: url("@/assets/cola.png");
}

.botol {
  width: 80px;
  height: 182px;
  margin-top: 29px;
  margin-bottom: 7px;

  background-image: url("@/assets/botol.png");
}

.barcode {
  width: 117px;
  height: 94px;
  margin-top: 73px;
  margin-bottom: 7px;
  margin-left: 22px;

  background-image: url("@/assets/barcode.png");
}

.pesan {
  width: 672px;
  height: 79px;
  margin-top: 73px;
  margin-left: 64px;

  font-weight: 700;
  font-size: 60px;
  line-height: 82px;
  text-align: center;

  color: #4c4c6d;
}

/* tb keperluan table bon */
.btn-checkout {
  width: 605px;
  height: 100px;
  border: transparent;
  background: #b8e0d8 !important;
  border-radius: 50px;

  font-style: normal;
  font-weight: 700;
  font-size: 48px;
  line-height: 65px;

  color: #4c4c6d;
}

.btn-checkout:hover {
  background: #7fa8a0;
  color: #4c4c6d;
}

.btn-checkout:active {
  background: #7fa8a0;
  color: black;
  border-color: transparent;
}

.btn-checkout:focus {
  background: #7fa8a0;
  color: black;
  border: transparent;
  box-shadow: none;
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

.bon-body {
  height: 500px;
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

/* tb */
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
.harga {
  text-align: right;
}

.barang {
  text-align: left;
}

h2 {
  font-weight: 400 !important;
  font-size: 48px !important;
  color: #4c4c6d !important;
}
</style>