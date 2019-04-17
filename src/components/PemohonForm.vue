<template>
    <div>
        <input type="text" class="d-none" v-model="recheck" />
        <div class="btn btn-block mb-2 text-uppercase text-white" :class="payment_status"><strong>{{ payment.status }}</strong></div>
      <div class="card mb-3 card-shadow">
        <div class="card-header text-left text-uppercase">MAKLUMAT PERIBADI</div>
        <div class="card-body">
          <div class="row text-left">
            <div class="col-sm-12">
              <div class="form-group">
                <label for>
                  Nama
                  
                </label>
                <input
                  type="text"
                  :value="info.nama"
                  class="form-control-plaintext text-uppercase"
                >
              </div>
            </div>

            <div class="col-sm-12 mb-3">
              <div class="form-groups">
                  <label>
                    Jantina
                  </label>
                  <input type="text" class="form-control-plaintext" :value="info.jantina">
                </div>
              </div>

            <div class="col-sm-6 text-left">
              <div class="form-group">
                <label>
                  Tempat Negara Lahir
                </label>
                <input type="text"
                v-model="info.tempat_lahir"
                class="form-control-plaintext"
                />
                
              </div>
            </div>

            <div class="col-sm-6 text-left">
              <div class="form-group">
                <label for>Tarikh Lahir</label>
                <input type="text" class="form-control-plaintext" 
                :value="info.tarikh_lahir"/>
              </div>
            </div>

            <div class="col-sm-6 text-left">
              <div class="form-group">
                <label for>
                  Warganegara
                  
                </label>
                <input type="text" 
                class="form-control-plaintext text-uppercase"
                :value="info.warganegara" />
              </div>
            </div>

            <div class="col-sm-6 text-left">
              <div class="form-group">
                <label>
                  Pekerjaan
                  
                </label>
                <input
                  type="text"
                  :value="info.pekerjaan"
                  class="form-control-plaintext text-uppercase"
                >
              </div>
            </div>

            <div class="col-sm-12 text-left">
              <div class="form-group mb-1">
                <label for>
                  Alamat
                  
                </label>
                <input
                  type="text"
                  name="alamat_1"
                  :value="info.alamat_1"
                  class="form-control-plaintext text-uppercase"
                >
              </div>
            </div>

            <div class="col-sm-12 text-left">
              <div class="form-group mb-1">
                <input
                  type="text"
                  v-model="info.alamat_2"
                  class="form-control-plaintext text-uppercase"
                >
              </div>
            </div>
            <div class="col-sm-12 text-left">
              <div class="form-group">
                <input
                  type="text"
                  name="alamat_3"
                  v-model="info.alamat_3"
                  class="form-control-plaintext text-uppercase"
                  autocomplete="off"
                >
              </div>
            </div>

            <div class="col-sm-12 mb-4">
              <div class="form-groups">
                  <label for>
                    Taraf Pekahwinan
                  </label>
                  <input type="text" 
                class="form-control-plaintext text-uppercase"
                :value="info.taraf_perkahwinan" />
                </div>
            </div>

            <div class="col-sm-12 col-md-6">
              <div class="form-group">
                <label for>
                  Email
                  
                </label>
                <input type="email" name="email" :value="info.email" 
                class="form-control-plaintext" >
              </div>
            </div>

            <div class="col-sm-12 col-md-6">
              <div class="form-group">
                <label for>
                  No Telefon
                </label>
                 <input type="text" 
                class="form-control-plaintext text-uppercase"
                :value="'+' + info.kod_negara + info.no_telefon" />
              </div>
            </div>
          </div>
        </div>
        </div>
      
      <div class="card mb-3 card-shadow">
        <div class="card-header text-left">
          <div>Maklumat Pasport perjalanan / dokumen perjalanan</div>
        </div>

        <div class="card-body">
          <div class="row text-left">
            <div class="col-sm-12 col-lg-6 text-left">
              <div class="form-group">
                <label for>
                  Jenis Dokumen Perjalanan
                  
                </label>
                <input type="text" 
                class="form-control-plaintext text-uppercase"
                :value="info.jenis_dokumen_perjalanan" />
              </div>
            </div>

            <div class="col-sm-12 col-lg-6 text-left">
              <div class="form-group">
                <label for>
                  Nombor
                  
                </label>
                <input
                  type="text"
                  name="nombor"
                  v-model="info.nombor"
                  required
                  class="form-control-plaintext text-uppercase"
                >
              </div>
            </div>

            <div class="col-sm-12 col-lg-6 text-left">
              <div class="form-group">
                <label for>
                  Tempat / Negara Dikeluarkan
                  
                </label>
                <input type="text" 
                class="form-control-plaintext text-uppercase"
                :value="info.negara_dikeluarkan" />
              </div>
            </div>

            <div class="col-sm-12 col-lg-6 text-left">
              <div class="form-group">
                <label for>Sah Sehingga</label>
                <input type="text" 
                class="form-control-plaintext text-uppercase"
                :value="info.sah_sehingga" />
              </div>
            </div>

          </div>
        </div>
      </div>
      </div>
    </div>
</template>

<script>
export default {
    name: "pemohon_form",
    props: {
        info: {},
        payment: {},
        recheck: String
    },
    data: function(){
        return {
            checked: "init",
            payment_status:  'btn-primary'
        }
    },
    mounted: function(){
        console.log("payment_status")
    },
    watch: {
        recheck: function(){
            switch(this.payment.status){
                case 'semakan': 
                this.payment_status = 'btn-warning'
                break;
                case 'paid':
                this.payment_status = "btn-success"
                break;
                case '':
                this.payment_status = "btn-danger"
                break;
            }
        }
    }

}
</script>
