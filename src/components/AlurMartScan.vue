<template>
  <div class="alur-mart">
    <div class="alur d-flex justify-content-center">
      <div class="wrapper-alur d-flex">
        <div class="icon-alur">
          <div class="scanBarcode"></div>
          <div class="paymentOp"></div>
          <div class="payment-alur"></div>
          <div class="transactionComplete"></div>
        </div>
        <div class="alurLine">
          <div class="Line"></div>
          <div class="ellipse"></div>
        </div>
        <div class="alurText d-flex justify-content-between">
          <div class="text-active">Scan<br />Barcode</div>
          <div class="text-non-active">Pilihan<br />Pembayaran</div>
          <div class="text-non-active">Pembayaran</div>
          <div class="text-non-active">Transaksi<br />Selesai</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AlurMartScan",
};
</script>

<style scoped>
.scanBarcode {
  background-image: url("@/assets/scanBarcodeG.png") !important;
}
</style>

<style>
.alur {
  width: 100%;
  height: 234px;
  background: #ffffff;
  box-shadow: -10px 10px 23px rgba(0, 0, 0, 0.25);
  border-radius: 30px;

  align-items: flex-end;
}

.wrapper-alur {
  display: flex;
  position: absolute;
  width: 955px;
  height: 209px;

  flex-direction: column;
}

.icon-alur {
  display: flex;
  width: 945px;
  height: 80px;
  /* flex-direction: row; */
}

.scanBarcode {
  position: absolute;
  width: 109px;
  height: 75px;
  margin-top: 3px;
  background-image: url("@/assets/scanBarcode.png");
}

.paymentOp {
  position: absolute;
  width: 74px;
  height: 74px;
  margin-left: 275px;
  margin-top: 4px;

  background-image: url("@/assets/paymentOp.png");
}

.payment-alur {
  position: absolute;
  width: 129px;
  height: 78px;
  margin-left: 551px;
  background-image: url("@/assets/payment.png");
}

.transactionComplete {
  position: absolute;
  width: 82px;
  height: 78px;
  margin-left: 863px;
  margin-top: 2px;
  background-image: url("@/assets/transactionComplete.png");
}

.alurLine {
  position: absolute;
  width: 894px;
  height: 40px;
  margin-left: 25px;
  margin-top: 92px;
}

.Line {
  position: absolute;
  width: 894px;
  height: 35px;
  left: 0px;
  margin-top: 2px;

  background-image: url("@/assets/line.png");
}

.ellipse {
  position: absolute;
  width: 40px;
  height: 40px;
  margin-top: 0px;
  margin-left: 0px;

  background-image: url("@/assets/Ellipse.png");
}

.alurText {
  position: absolute;
  width: 955px;
  height: 66px;
  top: 143px;

  font-style: normal;
  font-weight: 400;
  font-size: 24px;
  line-height: 33px;
}

.text-non-active {
  color: #cccccc;
}
</style>