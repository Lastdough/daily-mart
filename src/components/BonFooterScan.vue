<template>
  <div class="bon-footer-total">
    <table style="width: 100%; height: 123px" border="0">
      <tbody>
        <tr>
          <td style="" class="text-start">Sub Total</td>
          <td style="float: right; margin-right: 40px">
            Rp {{ formatPrice(calculateSubTotal()) }}
          </td>
        </tr>
        <tr>
          <td style="" class="text-start">PPN 11%</td>
          <td style="float: right; margin-right: 40px">
            Rp {{ formatPrice(calculatePPN(calculateSubTotal())) }}
          </td>
        </tr>
        <tr>
          <td style="" class="text-start">Total</td>
          <td style="float: right; margin-right: 40px">
            <b>Rp {{ formatPrice(calculateTotal()) }}</b>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "BonFooterScan",
  props: ["carts"],
  methods: {
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
</style>