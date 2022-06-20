<template>
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
                        Rp {{ formatPrice(calculatePPN(calculateSubTotal())) }}
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
                        {{ formatPrice(calculateTotal()) }}
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
</template>

<script>
export default {
  name: "BonFooterPay",
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