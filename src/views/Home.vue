<template>
  <div>
    <div class="row">
      <div class="col-md-5 text-left">
        <table style="height: 100%; width:100%">
  <tbody>
    <tr>
      <td class="align-middle">
        <form @submit.prevent="checkbarcode">
          <div class="form-group">
            <input ref="barcode_input" 
            type="text" class="form-control text-uppercase text-center" 
            v-model="pemohon_barcode"/>
          </div>
          <button type="submit" class="btn btn-block btn-primary d-none">
            check
          </button>
          </form>
      </td>
    </tr>
  </tbody>
</table>
      </div>
      <div class="col">
        <PemohonForm :info="info" :payment="payment" :recheck="recheck" />
      </div>
    </div>
  </div>
</template>

<style>
.barcode-form {
  margin: 0 auto;
}
</style>


<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import PemohonForm from "@/components/PemohonForm";
import Axios from 'axios';
import { API } from '@/Config';
import { maxHeaderSize } from 'http';

export default {
  name: "home",
  components: {
    HelloWorld,
    PemohonForm
  },
  data: function() {
    return {
      info: {},
      payment: {},
      recheck: "false",
      pemohon_barcode: "",
    }
  },
  mounted: function() {
    this.$refs.barcode_input.focus()
    Axios.get(API.baseurl +"register/info?regid=860636397&tempid=161034466" 
    ).then(response => {
      let resp = response.data.response
      this.info = resp.data_pemohon
      this.payment = resp.payment
      this.recheck = "true"
      console.log(resp)
    })
  },
  methods: {
    checkbarcode: function(){
      console.log(this.pemohon_barcode);
      this.pemohon_barcode = ""
    }
  }
};
</script>
