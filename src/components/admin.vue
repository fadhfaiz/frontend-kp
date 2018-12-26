<template>
  <div class="admin">
    <header>
      <nav class="navbar">
        <div style="width: 60%">
          <a
            href="./table"
          ><img id="logo" title="Maaf Tidak Ada Akses Keluar" src=../assets/img/back2.png style="margin: 0 15% 0 15%"></a>
          <div class="navbar-brand">Menu Admin |</div>
        </div>
        <br>
        <!-- <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                    aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
        </button>-->
      </nav>
    </header>
    <br>
    <div class="container">
      <div class="row">
        <div class="col align-self-center">
          <form>
            <div class="form-group">
              <label for="inputNama">Nama Siswa</label>
              <input type="text" class="form-control" ref="nama_siswa" id="inputNama" required>
              <small
                id="inputNama"
                class="form-text text-muted"
              >Setiap kata wajib diawali huruf kapital (Max 35 karakter).</small>
            </div>
            <div class="form-group">
              <label for="inputNIS">NIS Siswa</label>
              <input
                type="text"
                class="form-control"
                max="4"
                min="4"
                id="inputNIS"
                ref="nis"
                required
              >
            </div>
            <div class="form-group">
              <label for="inputKelas">Kelas Siswa</label>
              <!-- <input type="text" class="form-control" id="inputKelas"> -->
              <select class="form-control" id="inputKelas" ref="kelas">
                <option value>Pilih Kelas</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
                <option value="5">5</option>
                <option value="6">6</option>
              </select>
            </div>
          </form>
          <hr>
          <!-- Trigger -->
          <button
            type="button"
            class="btn btn-warning btn-block btn-lg"
            @click="tambahSiswa()"
          >Tambah Data Siswa</button>
          <hr>
          <a href="./dataSiswa" class="btn btn-success btn-block btn-lg">Lihat Data Siswa</a>
        </div>
        <div class="col align-self-center">
          <form>
            <div class="form-group">
              <label for="inputBuku">Judul Buku</label>
              <input type="text" class="form-control" id="inputBuku" ref="nama_buku">
              <small
                id="inputBuku"
                class="form-text text-muted"
              >Setiap kata wajib diawali huruf kapital.</small>
            </div>
            <div class="form-group">
              <label for="inputKodeBuku">Kode Buku</label>
              <input type="text" class="form-control" id="inputKodeBuku" ref="kode_buku">
            </div>
            <div class="form-group">
              <label for="inputHargaBuku">Harga Buku</label>
              <div class="input-group-prepend">
                <div class="input-group-text">Rp</div>
                <input type="number" class="form-control" id="inputHargaBuku" ref="harga">
              </div>
            </div>
          </form>
          <hr>
          <!-- Trigger -->
          <button
            type="button"
            class="btn btn-warning btn-block btn-lg"
            @click="tambahBuku()"
          >Tambah Data Buku</button>
          <hr>
          <a href="./dataBuku" class="btn btn-success btn-block btn-lg btn-mdf">Lihat Data Buku</a>
        </div>
        <div class="col align-self-center">
          <button
            type="button"
            class="btn btn-outline-dark btn-block btn-lg disabled my-3"
          >Tahap Pengembangan</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import swal from "sweetalert";
export default {
  name: "admin",
  data() {
    return {
      // siswa: []
      //buku: []
    };
  },
  methods: {
    tambahSiswa() {
      var banyakNama = this.$refs.nama_siswa.value;
      console.log(banyakNama.length);
      if (this.$refs.nama_siswa.value == "" || banyakNama.length > 35) {
        swal(
          "Perhatian!",
          "Maaf, Nama Siswa Tidak Boleh Kosong / Melebihi 35 Karakter",
          "error"
        );
      } else {
        var banyak = this.$refs.nis.value;
        if (banyak.length != 4) {
          swal("Perhatian!", "Maaf, NIS Harus 4 Karakter", "error");
        } else {
          axios.post("http://localhost:3000/api/dataSiswa", {
            nis: this.$refs.nis.value,
            nama_siswa: this.$refs.nama_siswa.value,
            kelas: this.$refs.kelas.value
          });
          swal("Terimakasih", "Data Berhasil Disimpan", "success");
          this.$refs.nis.value = "";
          this.$refs.nama_siswa.value = "";
          this.$refs.kelas.value = "";
        }
      }
    },

    tambahBuku() {
      var banyakJudul = this.$refs.nama_buku.value;
      console.log(banyakJudul.length);
      if (banyakJudul == "") {
        swal("Perhatian!", "Maaf, Judul Buku Tidak Boleh Kosong", "error");
      } else {
        var banyakKode = this.$refs.kode_buku.value;
        if (banyakKode.length != 3) {
          swal("Perhatian!", "Maaf, Kode Buku Hanya 3 Karakter", "error");
        } else {
          axios.post("http://localhost:3000/api/buku", {
            nama_buku: this.$refs.nama_buku.value,
            kode_buku: this.$refs.kode_buku.value,
            harga: this.$refs.harga.value
          });
          swal("Terimakasih", "Data Berhasil Disimpan", "success");
          this.$refs.nama_buku.value = "";
          this.$refs.kode_buku.value = "";
          this.$refs.harga.value = "";
        }
      }
    }
  }
};
</script>

<style>
@import url("../assets/css/bootstrap.min.css");
</style>