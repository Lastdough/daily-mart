<template>
  <div class="row mt-5">
    <!-- bagian item text pas di scan -->
    <div class="scannedItem">
      <table class="scannedItemTable">
        <tbody>
          <tr>
            <td>
              <span class="text-start">
                <h2>
                  {{ namaBarangScanned }}
                </h2>
              </span>
            </td>
            <td>
              <span class="text-end">
                <h2 v-if="hargaBarangScanned">
                  {{ "Rp " + formatPrice(hargaBarangScanned) }}
                </h2>
              </span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  <div class="row mt-5">
    <!-- static -->
    <div class="pesan-box">
      <div class="container d-flex" style="align-items: center">
        <div class="gambar">
          <div class="cola float-left"></div>
        </div>
        <div class="gambar">
        <div class="botol"></div>
        </div>
        <div class="gambar">
        <div class="barcode"></div>

        </div>
        <div class="pesan">Scan Barcode Barang</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ScannedItem",
  props: ["namaBarangScanned", "hargaBarangScanned"],
  methods: {
    formatPrice: function formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
  },
};
</script>

<style scoped>
.row {
  --bs-gutter-x: none;
}

.scannedItem {
  display: flex;
  align-items: center;

  width: 100%;
  height: 142px;
  /* left: 0px;
  top: 0px; */

  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.scannedItemTable {
  width: 100%;
  height: 79px;
  margin-top: 16px;
  margin-left: 43px;
  margin-right: 43px;
}
.pesan-box {
  display: flex;

  flex-direction: column;

  width: 100%;
  height: 218px;

  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;
}

.wrapper-pesan {
  position: absolute;
  width: 100%;
  height: 218px;
  left: 0px;
  top: 474px;
}

.cola {
  position: relative;
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
  /* height: auto; */
  height: 182px;
  margin-top: 29px;
  margin-bottom: 7px;

  background-image: url("@/assets/botol.png");
}

.barcode {
  width: 117px;
  /* height: auto; */
  height: 94px;
  margin-top: 73px;
  margin-bottom: 7px;
  margin-left: 22px;

  background-image: url("@/assets/barcode.png");
}

.pesan {
  width: 100%;
  height: 79px;
  margin-top: 13px;
  margin-left: 64px;

  font-weight: 700;
  font-size: 60px;
  line-height: 82px;
  text-align: center;

  color: #4c4c6d;
}
</style>