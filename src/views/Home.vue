<template>
  <div>
    <div class="row">
      <div class="col-md-5 no-print text-left">
        <table style="height: 100%; width:100%">
          <tbody>
            <tr>
              <td class="align-middle">
                <form @submit.prevent="checkbarcode">
                  <div class="form-group">
                    <div class="input-group">
                      <input
                        ref="barcode_input"
                        type="text"
                        class="form-control text-uppercase text-center"
                        v-model="pemohon_barcode"
                      >

                      <div class="input-group-append">
                        <button type="submit" class="btn btn-primary">
                          <i class="fas fa-angle-right"></i>
                        </button>
                      </div>
                    </div>
                  </div>
                </form>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col">
        <PemohonForm 
          class="no-print"
          :info="info"
          :payment="payment"
          :recheck="recheck"
          :appointment="appointment"
        />
        <div class="btn btn-block btn-primary no-print" @click="printForm">
          <i class="fa fa-print" aria-hidden="true"></i> Cetak Borang
        </div>
        <PrintForm class="print" :info="info" />
      </div>
    </div>
  </div>
</template>

<style>
.barcode-form {
  margin: 0 auto;
}

.print { 
  display: none;
}

@media print {
  .no-print {
    display: none;
  }
  .print {
    display: block
  }
  .card {
    border:none;
  }
}
</style>


<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import PemohonForm from "@/components/PemohonForm";
import Axios from "axios";
import { API } from "@/Config";
import { maxHeaderSize } from "http";
import PrintForm from "@/components/PrintForm";

export default {
  name: "home",
  components: {
    HelloWorld,
    PemohonForm,
    PrintForm
  },
  data: function() {
    return {
      info: {},
      payment: {
        status: "STATUS PEMBAYARAN"
      },
      recheck: "false",
      pemohon_barcode: "",
      appointment: "TARIKH TEMUJANJI"
    };
  },
  mounted: function() {
    this.$refs.barcode_input.focus();
  },
  methods: {
    checkbarcode: function() {
      Axios.get(
        API.baseurl + "register/info-temp-id?tempid=" + this.pemohon_barcode
      ).then(response => {
        let resp = response.data.response;
        console.log(resp)
        this.info = resp.data_pemohon;
        this.payment = resp.payment;
        this.appointment =
          resp.appointment.slot + " (" + resp.appointment.session + ")";
        this.recheck = "true";
        this.pemohon_barcode = "";
      });
    },
    printForm: function() {
      window.print();
    }
  }
};
</script>
