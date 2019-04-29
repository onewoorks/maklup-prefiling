<template>
  <div class="formPrint">
    <div class="card">
      <div class="card-body">
        <div class="text-left">
          <div class="row text-center formName mb-3">
            <div class="col-3"></div>
            <div class="col-9 p-3" style="border:1px solid #000">
              <div><strong>JABATAN IMIGRESEN MALAYSIA</strong></div>
              <div><strong>BORANG PERMOHONAN VISA</strong></div>
              <div>
                <i>VISA APPLICATION FORM</i>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="col-8">
              <div class="row">
                <div class="col-4">
                  <div>*Jenis Permohonan</div>
                  <div>
                    <i>Type of Application</i>
                  </div>
                </div>
                <div class="col-3">
                  <div>Dalam Malaysia</div>
                  <div>
                    <i>In Malaysia</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
                <div class="col-3">
                  <div>Seberang Laut</div>
                  <div>
                    <i>Oversea</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
              </div>
              <div class="row header">
                <div class="col-12">
                  <div>A. MAKLUMAT PERMOHONAN</div>
                  <div>
                    <i>PARTICULAR OF APPLICANT</i>
                  </div>
                </div>
              </div>

              <div class="row">
                <div class="col-12">
                  <div>Nama Penuh (Huruf Besar)</div>
                  <div>
                    <i>Full Name (Capital Letter)</i>
                  </div>
                  <div></div>
                </div>
              </div>

              <div class="row pl-3">
                <div class="col-12 dataBox">
                  <div style='line-height:36px'>{{ info.nama }} &nbsp;</div>
                </div>
              </div>
            </div>

            <div class="col-4"></div>
          </div>

          <div class="row text-left">
            <div class="col-2">
              <div>Jantina</div>
              <div>
                <i>Gender</i>
              </div>
            </div>
            <div class="col-2">
              <div>Lelaki</div>
              <div>
                <i>Male</i>
              </div>
            </div>
            <div class="col-1 dataBox cross-option">
              <div v-if="info.jantina=='LELAKI'">
                <i class="fa fa-times" aria-hidden="true"></i>
              </div>
            </div>

            <div class="col-2">
              <div>Perempuan</div>
              <div>
                <i>Female</i>
              </div>
            </div>

            <div class="col-1 dataBox cross-option">
              <div v-if="info.jantina=='PEREMPUAN'">
                <i class="fas fa-times fa-3x"></i>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Tempat/Negara Lahir</div>
              <div>
                <i>Place/Country of Birth</i>
              </div>
            </div>

            <div class="col-3 dataBox">
              {{ info.tempat_lahir }}
            </div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>**Tarikh Lahir</div>
              <div>
                <i>Date of Birth</i>
              </div>
            </div>
            <div class="col-3 dataBox">
              {{ info.tarikh_lahir }}
            </div>
            <div class="col-3">
              <div>Warganegara</div>
              <div>
                <i>Nationality</i>
              </div>
            </div>
            <div class="col-3 dataBox">{{ info.warganegara }}</div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Pekerjaaan</div>
              <div>
                <i>Occupation</i>
              </div>
            </div>
            <div class="col-3 dataBox">{{ info.pekerjaan}}</div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Alamat</div>
              <div>
                <i>Address</i>
              </div>
            </div>
            <div class="col-9 dataBox">
              <div>{{ info.alamat_1 }}</div>
              <div>{{ info.alamat_2 }}</div>
              <div>{{ info.alamat_3 }}</div>
            </div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Taraf Perkahwinanan</div>
              <div>
                <i>Maritak Status</i>
              </div>
            </div>
            <div class="col-2">
              <div>Belum Berkahwin</div>
              <div>
                <i>Single</i>
              </div>
            </div>

            <div class="col-1 dataBox cross-option">
              <div v-if="info.taraf_perkahwinan=='BELUM BERKAHWIN'">
                <i class="fa fa-times" aria-hidden="true"></i>
              </div>
            </div>

            <div class="col-2">
              <div>Berkahwin</div>
              <div>
                <i>Married</i>
              </div>
            </div>
            <div class="col-1 dataBox cross-option">
              <div v-if="info.taraf_perkahwinan == 'BERKAHWIN'">
                <i class="fa fa-times" aria-hidden="true"></i>
              </div>
            </div>
          </div>

          <div class="row header">
            <div class="col-12">
              <div>MAKLUMAT PASPORT PERJALANAN / DOKUMEN PERJALANAN</div>
              <div>
                <i>PARTICULARS OF PASSPORT / TRAVEL DOCUMENT</i>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Jenis Dokumen Perjalanan</div>
              <div>
                <i>Type Of Travel Document</i>
              </div>
            </div>
            <div class="col-3 dataBox">{{ info.jenis_dokumen_perjalanan }}</div>

            <div class="col-3">
              <div>Nombor</div>
              <div>
                <i>Number</i>
              </div>
            </div>
            <div class="col-3 dataBox">{{ info.number }}</div>
          </div>

          <div class="row">
            <div class="col-3 pr-0">
              <div>Tempat/Negara Dikeluarkan</div>
              <div>
                <i>Place / Country Of Issue</i>
              </div>
            </div>
            <div class="col-3 dataBox">
              <div class="align-self-center">
{{ info.negara_dikeluarkan }}
              </div>
              </div>

            <div class="col-3">
              <div>**Sah Sehingga</div>
            </div>
            <div class="col-3 dataBox">
              {{ info.sah_sehingga }}
            </div>
          </div>

          <div class="row header">
            <div class="col-12">
              <div>BUTIR - BUTIR PENGANJUR DI MALAYSIA</div>
              <div>
                <i>PARTICULARS OF SPONSER IN MALAYSIA</i>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Nama Penuh (Huruf Besar)</div>
              <div>
                <i>Full Name (Capital Letter</i>
              </div>
            </div>
            <div class="col-9 dataBox"></div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>No Kad Pengenalan</div>
              <div>
                <i>NRIC</i>
              </div>
            </div>
            <div class="col-3 dataBox"></div>
            <div class="col-3">
              <div>No Telefon</div>
              <div>
                <i>Telephone No</i>
              </div>
            </div>
            <div class="col-3 dataBox"></div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Alamat</div>
              <div>
                <i>Address</i>
              </div>
            </div>
            <div class="col-9 dataBox"></div>
          </div>

          <div class="row header">
            <div class="col-12">
              <div>BUTIR- BUTIR PERMOHONAN</div>
              <div>
                <i>DETAIL OF APPLICATION</i>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Tempoh Tinggal Yang Dicadangkan</div>
              <div>
                <i>Duration Of Proposed Stay</i>
              </div>
            </div>
            <div class="col-3"></div>
            <div class="col-2">
              <div>Bulan</div>
              <div>
                <i>Month</i>
              </div>
            </div>
            <div class="col-4 dataBox"></div>
          </div>

          <div class="row">
            <div class="col-3">
              <div>Tujuan Perjalanan</div>
              <div>
                <i>Purposed Of Journey</i>
              </div>
            </div>
            <div class="col-9">
              <div class="row">
                <div class="col-5">
                  <div>Bercuti</div>
                  <div>
                    <i>Holiday</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
                <div class="col-5">
                  <div>Transit</div>
                  <div>
                    <i>Transit</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
              </div>
              <div class="row">
                <div class="col-5">
                  <div>Urusan Perniagaan</div>
                  <div>
                    <i>Business</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
                <div class="col-5">
                  <div>Urusan Rasmi</div>
                  <div>
                    <i>Official Trip</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
              </div>
              <div class="row">
                <div class="col-5">
                  <div>Melawat Saudara Mara / Kawan</div>
                  <div>
                    <i>Visiting Relatives / Friends</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
                <div class="col-5">
                  <div>Persidangan</div>
                  <div>
                    <i>Conference</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
              </div>
              <div class="row">
                <div class="col-5">
                  <div>Bekerja</div>
                  <div>
                    <i>Employment</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
                <div class="col-3">
                  <div>Lain-lain (Nyatakan)</div>
                  <div>
                    <i>Other (Specify)</i>
                  </div>
                </div>
                <div class="col-3 dataBox"></div>
              </div>
              <div class="row">
                <div class="col-5">
                  <div>Belajar</div>
                  <div>
                    <i>Study</i>
                  </div>
                </div>
                <div class="col-1 dataBox"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.formPrint {
  font-size: 0.8rem;
}

.formPrint .formName {
  font-size: 1rem;
}

.formPrint .cross-option {
  text-align: center;
  font-size: 1rem
}

.formPrint .header {
  font-weight: bold;
  background-color: #dedede;
  margin-top: 10px;
  margin-bottom: 10px;
}
.formPrint .row {
  padding: 7px 0;
}

.formPrint i {
  font-size: 0.7rem;
}
.formPrint .dataBox {
  border: 1px solid #000;
  padding:4px;
  text-transform: uppercase;
}

@media print {
  .formPrint .header {
    background-color:  #dedede;
  }
  .formPrint .row {
  padding: 5px 0;
}
}
</style>


<script>
export default {
  name: "print_form",
  props: {
    info: Object
  }
};
</script>

<style>
</style>
