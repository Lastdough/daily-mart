<template>
  <div class="scan-view pt-2 ps-2">
    <HeaderMart />
    <div class="container-fluid mt-3">
      <div class="row">
        <!-- 12 kolom -->
        <!-- 4 deret mulai -->
        <!-- KIRI -->
        <div class="col-md-auto">
          <div class="row">
            <!-- bagian alur beli -->
            <component :is="alur" />
            <!-- <AlurMartScan /> -->
          </div>
          <component
            :is="rowBawah"
            :namaBarangScanned="namaBarangScanned"
            :hargaBarangScanned="hargaBarangScanned"
          />
          <div class="row mt-4">
            <div class="tombol d-flex justify-content-center">
              <div class="tombol-wrapper d-flex align-items-center">
                <div class="settings"></div>
                <div class="help"></div>
                <div class="interface-click-able">
                  <div class="col">
                    <div class="input-group mb-3" v-if="!isInputHidden">
                      <input
                        type="text"
                        class="form-control"
                        placeholder="Masukkan Kode Barcode"
                        autofocus
                        v-model="barcode"
                        v-on:keyup.enter="scanItem()"
                        ref="search"
                      />
                    </div>
                  </div>
                  <div class="col">
                    <div class="back" v-if="true">
                      <router-link to="">
                        <button
                          type="button"
                          class="btn-primary btn-back"
                          v-if="!isBackHidden"
                          @click="
                            (alur = 'AlurMartScan'),
                              (rowBawah = 'ScannedItem'),
                              (isCheckoutHidden = false),
                              (isBackHidden = true),
                              (isInputHidden = false),
                              (bonFooter = 'BonFooterScan'),
                              (bodyHeight = '500px')
                          "
                        >
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
        </div>
        <!-- KANAN -->
        <!-- tabel bon -->
        <div class="col-md-3half">
          <div class="">
            <div class="bon">
              <!-- <div class="bon-header py-4">
              <div class="">
                <table class="mx-3" border="0" style="width:100%">
                  <tbody>
                    <tr class="">
                      <td style="width: 40%;">
                        <div class="row-content">
                          <h4><b>Nama Barang</b></h4>
                       </div>
                      </td>
                      <td style="width: 40%;" >
                        <div class="row-content">
                          <div class="text-end ">
                            <h4><b>Harga Barang</b></h4>
                         </div>
                         </div>
                      </td>
                      <td style="width: 10%;">&nbsp;</td>
                      <td style="width: 10%;"></td>
                    </tr>
                  </tbody>
                </table>
              </div> -->
              <div class="bon-header d-flex align-items-end text-left">
                <div class="d-flex align-items-end mb-3">
                  <table class="" border="0">
                    <tbody>
                      <tr>
                        <td style="width: 350px">
                          <div class="row-content">
                            <span class="text-start">
                              <h4>Nama Barang</h4>
                            </span>
                          </div>
                        </td>
                        <td style="width: 183px">
                          <div class="row-content">
                            <!-- <div class="text-end">
                            </div> -->
                            <span class="text-end">
                              <h4>Harga Barang</h4>
                            </span>
                          </div>
                        </td>
                        <td style="width: 60px">&nbsp;</td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
              <!-- bon body -->
              <BonBody :carts="carts" :index="index" :bodyHeight="bodyHeight" />
              <div class="bon-footer">
                <component :is="bonFooter" :carts="carts" />
                <div class="bon-footer-checkout mt-4">
                  <router-link to="">
                    <button
                      type="button"
                      class="btn btn-primary btn-checkout btn-lg"
                      v-if="!isCheckoutHidden"
                      @click="
                        (alur = 'AlurMartMet'),
                          (rowBawah = 'PaymentMethod'),
                          (isCheckoutHidden = true),
                          (isBackHidden = false),
                          (isInputHidden = true),
                          (bonFooter = 'BonFooterPay'),
                          (bodyHeight = '600px')
                      "
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
    </div>
    <FooterCopyright />
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderMart from "@/components/HeaderMart.vue";

import AlurMartScan from "@/components/AlurMartScan.vue";
import AlurMartMet from "@/components/AlurMartMet.vue";
import ScannedItem from "@/components/ScannedItem.vue";
import BonBody from "@/components/BonBody.vue";
import BonFooterScan from "@/components/BonFooterScan.vue";
import BonFooterPay from "@/components/BonFooterPay.vue";
import PaymentMethod from "@/components/PaymentMethod.vue";

import FooterCopyright from "@/components/FooterCopyright.vue";

// data :
import barangData from "@/assets/barang.json";
BonFooterScan;
export default {
  name: "MainView",
  components: {
    HeaderMart,
    // component Alur
    AlurMartScan,
    AlurMartMet,
    // AlurMartPay,
    // AlurMartFin



    // component Scanned Item
    ScannedItem,

    // component bon
    BonBody,
    BonFooterScan,
    BonFooterPay,

    /**
     * Component Metode Pembayaran
     **/ 
    PaymentMethod,
    // CashMethod,
    // CreditMethod,
    // QrisMethod,
    // GopayMethod,
    // OvoMethod,
    // ShopeeMethod,


    // component transaksi selesai
    // TransaksiSelesai,

    FooterCopyright,
  },
  data() {
    return {
      barcode: "",
      namaBarangScanned: "",
      hargaBarangScanned: "",

      carts: [],

      alur: "AlurMartScan",
      rowBawah: "ScannedItem",

      bodyHeight: "500px",
      bonFooter: "BonFooterScan",

      isCheckoutHidden: false,
      isBackHidden: true,

      isInputHidden: false,
    };
  },
  methods: {
    setFocus: function () {
      // Note, you need to add a ref="search" attribute to your input.
      this.$refs.search.focus();
    },

    scanItem: function () {
      //memanggil json barang.json
      let serializedData = barangData;

      //membandingkan nilai barcode dengan data json
      let match = serializedData.find((el) => el.barcode == this.barcode);
      if (match) {
        //ditambahkan ke keranjang
        this.carts.push({
          nama: match.nama,
          harga: match.harga,
          barcode: match.barcode,
        });

        this.namaBarangScanned = match.nama;
        this.hargaBarangScanned = match.harga;
        this.barcode = "";
        console.log("Result:", match.nama);
      }
      //jika barang tidak ditemukan
      else {
        this.barcode = "";
        alert("Maaf, Barang tidak ditemukan");
      }
    },
    formatPrice: function formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
    calculateSubTotal: function calculateSubTotal() {
      return this.carts
        .map((item) => item.harga)
        .reduce((prev, curr) => prev + curr, 0);
    },
    calculatePPN: function calculatePPN(value) {
      let ppn = value * (11 / 100);
      return ppn;
    },
    calculateTotal: function calculateTotal() {
      let subTotal = this.carts
        .map((item) => item.harga)
        .reduce((prev, curr) => prev + curr, 0);
      let total = subTotal + subTotal * (11 / 100);
      return total;
    },
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
  width: 100%;
  height: 894px;
  left: 47px;
  top: 160px;
}
.row {
  --bs-gutter-x: 0;
  border-radius: 30px;
}
.row-body .row-body-left {
  width: 100%;
}

.scan-view {
  height: 100%;
  width: 100%;
}

/* tb keperluan table bon */
.btn-checkout {
  width: 90%;
  /* width: 605px; */
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
  color: #4c4c6d;
  border-color: transparent;
}

.btn-checkout:focus {
  background: #7fa8a0;
  color: #4c4c6d;
  border: transparent;
  box-shadow: none;
}

.bon {
  width: 100%;
  height: 875px;
  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.bon-header {
  /* display: flex; */
  /* align-items: end; */
  width: 100%;
  height: 98px;
  /* vertical-align: baseline; */
  background: #dedede;
  border-radius: 30px 30px 0px 0px;
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