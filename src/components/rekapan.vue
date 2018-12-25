<template>
  <div class="rekapan">
    <header>
      <nav class="navbar">
        <div style="width: 60%">
          <a
            href="/table"
          ><img id="logo" title="tombol untuk kembali ke halaman utama" src=../assets/img/back2.png style="margin: 0 15% 0 15%"></a>
          <div class="navbar-brand">{{data[0].nama}} | {{data[0].nis}}</div>
        </div>
        <br>
        <!-- <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
			    aria-expanded="false" aria-label="Toggle navigation">
				<span class="navbar-toggler-icon"></span>
        </button>-->
      </nav>
    </header>

    <!-- Modal -->
    <div
      class="modal fade"
      id="bayarDonatur"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document" style="width: 800px !important">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Bayar Donatur</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body" style="width: 700px !important">
            <div id="atas1" style="padding: -100px !important">
              <input type="checkbox" value="januari"> Januari
              <br>
              <input type="checkbox" value="februari"> Februari
              <br>
              <input type="checkbox" value="maret"> Maret
              <br>
              <input type="checkbox" value="april"> April
              <br>
              <input type="checkbox" value="mei"> Mei
              <br>
              <input type="checkbox" value="juni"> Juni
              <br>
            </div>
            <div id="atas2">
              <input type="checkbox" value="juli"> Juli
              <br>
              <input type="checkbox" value="agustus"> Agustus
              <br>
              <input type="checkbox" value="september"> September
              <br>
              <input type="checkbox" value="oktober"> Oktober
              <br>
              <input type="checkbox" value="november"> November
              <br>
              <input type="checkbox" value="desember"> Desember
              <br>
            </div>
          </div>
          <span style="padding-left: 20px">Total Biaya</span>
          <input type="number" class v-model="bayar">
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Tutup</button>
            <button type="button" class="btn btn-primary" @click.prevent="bayarwoi">Bayar</button>
          </div>
        </div>
      </div>
    </div>

    <div
      class="modal fade"
      id="bayar_pengembangan"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Bayar Pengembangan</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div id="atas1">
              <input type="checkbox" value="januari"> Januari
              <br>
              <input type="checkbox" value="februari"> Februari
              <br>
              <input type="checkbox" value="maret"> Maret
              <br>
              <input type="checkbox" value="april"> April
              <br>
              <input type="checkbox" value="mei"> Mei
              <br>
              <input type="checkbox" value="juni"> Juni
              <br>
            </div>
            <div id="atas2">
              <input type="checkbox" value="juli"> Juli
              <br>
              <input type="checkbox" value="agustus"> Agustus
              <br>
              <input type="checkbox" value="september"> September
              <br>
              <input type="checkbox" value="oktober"> Oktober
              <br>
              <input type="checkbox" value="november"> November
              <br>
              <input type="checkbox" value="desember"> Desember
              <br>
            </div>
          </div>
          <span style="padding-left: 20px">Total Biaya</span>
          <input type="number" class v-model="bayar">
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Tutup</button>
            <button type="button" class="btn btn-primary" @click.prevent="bayarwoi">Bayar</button>
          </div>
        </div>
      </div>
    </div>

    <div
      class="modal fade"
      id="bayar_les"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Bayar Les</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div id="atas1">
              <input type="checkbox" value="januari"> Januari
              <br>
              <input type="checkbox" value="februari"> Februari
              <br>
              <input type="checkbox" value="maret"> Maret
              <br>
              <input type="checkbox" value="april"> April
              <br>
              <input type="checkbox" value="mei"> Mei
              <br>
              <input type="checkbox" value="juni"> Juni
              <br>
            </div>
            <div id="atas2">
              <input type="checkbox" value="juli"> Juli
              <br>
              <input type="checkbox" value="agustus"> Agustus
              <br>
              <input type="checkbox" value="september"> September
              <br>
              <input type="checkbox" value="oktober"> Oktober
              <br>
              <input type="checkbox" value="november"> November
              <br>
              <input type="checkbox" value="desember"> Desember
              <br>
            </div>
          </div>
          <span style="padding-left: 20px">Total Biaya</span>
          <input type="number" class v-model="bayar">
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Tutup</button>
            <button type="button" class="btn btn-primary" @click.prevent="bayarwoi">Bayar</button>
          </div>
        </div>
      </div>
    </div>

    <div
      class="modal fade"
      id="bayar_buku"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Bayar Buku</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div id="atas1">
              <input type="checkbox" value="januari"> Januari
              <br>
              <input type="checkbox" value="februari"> Februari
              <br>
              <input type="checkbox" value="maret"> Maret
              <br>
              <input type="checkbox" value="april"> April
              <br>
              <input type="checkbox" value="mei"> Mei
              <br>
              <input type="checkbox" value="juni"> Juni
              <br>
            </div>
            <div id="atas2">
              <input type="checkbox" value="juli"> Juli
              <br>
              <input type="checkbox" value="agustus"> Agustus
              <br>
              <input type="checkbox" value="september"> September
              <br>
              <input type="checkbox" value="oktober"> Oktober
              <br>
              <input type="checkbox" value="november"> November
              <br>
              <input type="checkbox" value="desember"> Desember
              <br>
            </div>
          </div>
          <span style="padding-left: 20px">Total Biaya</span>
          <input type="number" class v-model="bayar">
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Tutup</button>
            <button type="button" class="btn btn-primary" @click.prevent="bayarwoi">Bayar</button>
          </div>
        </div>
      </div>
    </div>

    <div
      class="modal fade"
      id="bayar_tpa"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Bayar TPA</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div id="atas1">
              <input type="checkbox" value="januari"> Januari
              <br>
              <input type="checkbox" value="februari"> Februari
              <br>
              <input type="checkbox" value="maret"> Maret
              <br>
              <input type="checkbox" value="april"> April
              <br>
              <input type="checkbox" value="mei"> Mei
              <br>
              <input type="checkbox" value="juni"> Juni
              <br>
            </div>
            <div id="atas2">
              <input type="checkbox" value="juli"> Juli
              <br>
              <input type="checkbox" value="agustus"> Agustus
              <br>
              <input type="checkbox" value="september"> September
              <br>
              <input type="checkbox" value="oktober"> Oktober
              <br>
              <input type="checkbox" value="november"> November
              <br>
              <input type="checkbox" value="desember"> Desember
              <br>
            </div>
          </div>
          <span style="padding-left: 20px">Total Biaya</span>
          <input type="number" class v-model="bayar">
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Tutup</button>
            <button type="button" class="btn btn-primary" @click.prevent="bayarwoi">Bayar</button>
          </div>
        </div>
      </div>
    </div>

    <div
      class="modal fade"
      id="bayar_ekstra"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >x
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Bayar Ekstra</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div id="atas1">
              <input type="checkbox" value="januari"> Januari
              <br>
              <input type="checkbox" value="februari"> Februari
              <br>
              <input type="checkbox" value="maret"> Maret
              <br>
              <input type="checkbox" value="april"> April
              <br>
              <input type="checkbox" value="mei"> Mei
              <br>
              <input type="checkbox" value="juni"> Juni
              <br>
            </div>
            <div id="atas2">
              <input type="checkbox" value="juli"> Juli
              <br>
              <input type="checkbox" value="agustus"> Agustus
              <br>
              <input type="checkbox" value="september"> September
              <br>
              <input type="checkbox" value="oktober"> Oktober
              <br>
              <input type="checkbox" value="november"> November
              <br>
              <input type="checkbox" value="desember"> Desember
              <br>
            </div>
          </div>
          <span style="padding-left: 20px">Total Biaya</span>
          <input type="number" class v-model="bayar">
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Tutup</button>
            <!-- <button type="button" class="btn btn-primary" @click.prevent="bayarwoi">Bayar</button> -->
          </div>
        </div>
      </div>
    </div>

    <div class="container" id="app">
      <div class="test">
        <br>
        <div class="atas">
          <div class="kanan"></div>

          <div class="kiri">
            <div class="row">
              <div class="form-group col-3"></div>
              <div class="col-3"></div>
              <div class="col-3">
                <input type="text" disabled v-model="tanggal">
              </div>
              <div class="col-3 container">
                <button class="btn btn-warning btn-block" @click="cetakNota">Cetak</button>
              </div>
            </div>
          </div>
          <br>

          <div class="bawah">
            <table class="table table-striped table-bordered">
              <thead class="thead-dark">
                <tr>
                  <th scope="col">Donatur</th>
                  <th scope="col">Pengembangan</th>
                  <th scope="col">Les</th>
                  <th scope="col">Buku</th>
                  <th scope="col">TPA</th>
                  <th scope="col">Ekstra</th>
                </tr>
              </thead>
              <tbody>
                <tr :key="x" v-for="x in data">
                  <td>
                    {{ x.donatur}}
                    <br>
                    <!-- <button v-on:click="bayar_donatur(x.id)">Bayar</button> -->
                    <button
                      type="button"
                      class="btn btn-primary"
                      data-toggle="modal"
                      data-target="#bayarDonatur"
                      @click="bayar_donatur(x.nis)"
                    >Bayar</button>
                  </td>
                  <td>
                    {{ x.pengembangan }}
                    <br>
                    <button
                      type="button"
                      class="btn btn-primary"
                      data-toggle="modal"
                      data-target="#bayar_pengembangan"
                    >Bayar</button>
                  </td>
                  <td>
                    {{ x.les }}
                    <br>
                    <button
                      type="button"
                      class="btn btn-primary"
                      data-toggle="modal"
                      data-target="#bayar_les"
                    >Bayar</button>
                  </td>
                  <td>
                    {{ x.buku }}
                    <br>
                    <button
                      type="button"
                      class="btn btn-primary"
                      data-toggle="modal"
                      data-target="#bayar_buku"
                    >Bayar</button>
                  </td>
                  <td>
                    {{ x.tpa }}
                    <br>
                    <button
                      type="button"
                      class="btn btn-primary"
                      data-toggle="modal"
                      data-target="#bayar_tpa"
                    >Bayar</button>
                  </td>
                  <td>
                    {{ x.ekstra }}
                    <br>
                    <button
                      type="button"
                      class="btn btn-primary"
                      data-toggle="modal"
                      data-target="#bayar_ekstra"
                    >Bayar</button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="alert alert-success">
        <strong>Donatur :</strong> Merupakan tagihan yang digunakan ...
      </div>

      <div class="alert alert-success">
        <strong>Pengembangan :</strong> Merupakan dana yang digunakan ...
      </div>

      <div class="alert alert-success">
        <strong>Les :</strong> Merupakan tagihan yang digunakan ...
      </div>

      <div class="alert alert-success">
        <strong>Buku :</strong> Merupakan tagihan yang digunakan ...
      </div>
    </div>
  </div>
</template>

<script>
// import VueRouter from 'vue-router'
import swal from "sweetalert";
import axios from "axios";
// Vue.use(VueRouter)

// var router = new VueRouter()
export default {
  name: "rekapan",
  data() {
    return {
      tampil: false,
      d: new Date(),
      bayar: "",
      data: [],
      pembayaran: [],
      kode: ""
    };
  },
  created() {
    axios.get("http://localhost:3000/api/dataSiswa").then(res => {
      this.pembayaran = res.data;
      console.log(res.data);
      var kode = window.location.pathname;
      // var res = kode.slice(9,13)
      console.log(kode.slice(9, 13));
      this.fetchRekapan(kode.slice(9, 13));
    });
  },
  filters: {
    capitalize: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    }
  },

  mounted() {
    // var kode = window.location.pathname
    // // var res = kode.slice(9,13)
    // console.log(kode.slice(9,13));
    // this.fetchRekapan(kode.slice(9,13));
  },
  computed: {
    tanggal() {
      // return `Tanggal : ${this.d.getDate()} / ${this.d.getMonth() + 1} / ${this.d.getFullYear()}`
      return this.d.toDateString();
      // var xnama = siswa.nama_siswa.charAt(0).toUpperCase() + siswa.nama_siswa.slice(1);
      // var xnama = siswa.nama_siswa.toLowerCase();
      // return siswa.nis.match(this.cari) || siswa.nama_siswa.match(this.cari) || xnama.match(this.cari);
    }
  },
  methods: {
    fetchRekapan(id) {
      // this.$http.get('http://localhost/rekapan/')
      this.pembayaran.forEach(el => {
        // console.log(el.nama_siswa, el.nis)
        if (el.nis == id) {
          this.data.push({
            nis: el.nis,
            nama: el.nama_siswa,
            kelas: el.kelas,
            donatur: 100000,
            pengembangan: 100000,
            les: 100000,
            buku: 100000,
            tpa: 100000,
            ekstra: 100000
          });
        }
      });
    },
    gajadi: function() {
      this.tampil = this.tampil;
      console.log(this.tampil);
    },
    iya: function() {
      this.tampil = !this.tampil;
      console.log(this.tampil);
    },
    cetakNota: function() {
      window.print();
    },
    bayar_donatur: function(id) {
      this.iya();
    },
    bayar_pengembangan: function(id) {
      this.iya();
    },
    bayar_les: function(id) {
      this.iya();
    },
    bayar_buku: function(id) {
      this.iya();
    },
    bayarwoi: function(id) {
      this.iya();
    }
  }
};
</script>

<style scope>
@import url("../assets/css/bootstrap.min.css");
@import url("../assets/css/pembayaran.css");
</style>