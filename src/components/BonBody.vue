<template>
  <div class="bon-body">
    <div
      class="bon-body-row"
      v-for="(barangTable, index) in carts"
      v-bind:key="barangTable.id"
    >
      <table class="bon-body-row-table" border="0">
        <tbody>
          <tr>
            <td style="width: 40%">
                <div class="row-content">
                  {{ barangTable.nama }}
                </div>
            </td>
            <td style="width: 40%">
              <div class="row-content">
                <div class="text-end">
                  {{ formatPrice(barangTable.harga) }}
                </div>
              </div>
            </td>
            <td style="">&nbsp;</td>
            <td style="">
              <!-- catatan : tombol yang buat remove -->
              <button
                v-on:click="removeItem(carts, index)"
                class="btn btn-cancel"
              >
                <div class="cancel"></div>
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "BonBody",
  props: ["carts", "index", "bodyHeight"],
  methods: {
    removeItem: function (carts, index) {
      carts.splice(index, 1);
    },
    formatPrice: function formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
  },
};
</script>


<style>
.bon-body {
  height: v-bind('bodyHeight');
  overflow-x: hidden; /* Hide horizontal scrollbar */
  overflow-y: auto;
}
</style>

<style scoped>

.bon-body-row {
  width: 100%;

  left: 0px;
  top: 0px;
  margin-top: 12px;
  background: #f4f4f4;
}

.bon-body-row-table {
  width: 100%;
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
</style>
