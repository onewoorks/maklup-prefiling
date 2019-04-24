<template>
    <div>
        <input type="text" class="d-none" v-model="recheck" />
        <div class="btn btn-block mb-2 text-uppercase text-white" 
        :class="payment_status"><strong>{{ payment.status }}</strong></div>
        <div class="btn btn-block mb-2 mb-2 text-uppercase text-white" 
        :class="payment_status"><strong>{{ appointment }}</strong></div>
      <div class="card mb-3 card-shadow">
        <div class="card-header text-left text-uppercase">MAKLUMAT PERIBADI</div>
        <div class="card-body text-left">
          <table class="table">
            <tbody>
              <tr>
                <th>Nama</th>
                <td colspan="3" class='text-uppercase'>{{ info.nama }}</td>
              </tr>
              <tr>
                <th>Jantina</th>
                <td colspan="3">{{ info.jantina }}</td>
              </tr>

              <tr>
                <th>Tempat Negara Lahir</th>
                <td>{{ info.tempat_lahir }}</td>
                <th>Tarikh Lahir</th>
                <td>{{ info.tarikh_lahir }}</td>
              </tr>

              <tr>
                <th>Warganegara</th>
                <td>{{ info.warganegara}}</td>
                <th>Pekerjaan </th>
                <td>{{ info.pekerjaan }}</td>
              </tr>

              <tr>
                <th>Alamat</th>
                <td colspan="3" class='text-uppercase'>
                  <div>{{ info.alamat_1 }} </div>
                  <div>{{ info.alamat_2 }}</div>
                  <div>{{ info.alamat_3 }}</div>
                </td>
              </tr>
              <tr>
                <th>Taraf Perkahwinan</th>
                <td>{{ info.taraf_perkahwinan}}</td>
                <td></td>
                <td></td>
              </tr>

              <tr>
                <th>Email</th>
                <td>{{ info.email }}</td>
                <th>No Telefon </th>
                <td>+{{ info.kod_negara + info.no_telefon }}</td>
              </tr>

              <tr>
                <th colspan="4">Maklumat Dokumen Perjalanan</th>
              </tr>

              <tr>
                <th>Jenis Dokumen</th>
                <td>{{ info.jenis_dokumen_perjalanan }}</td>
                <th>Nombor</th>
                <td class='text-uppercase'>{{ info.nombor}}</td>
              </tr>

              <tr>
                <th>Tempat / Negara Dikeluarkan</th>
                <td>{{ info.negara_dikeluarkan }}</td>
                <th>Sah Sehingga </th>
                <td>{{ info.sah_sehingga}}</td>
              </tr>
            </tbody>
          </table>
        </div>
        </div>
      
    </div>
</template>

<script>
export default {
    name: "pemohon_form",
    props: {
        info: Object,
        payment: Object,
        appointment: String,
        recheck: String
    },
    data: function(){
        return {
            checked: "init",
            payment_status:  'btn-secondary'
        }
    },
    mounted: function(){
        console.log(this.payment_status)
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
