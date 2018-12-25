<template>
  <div class="admin">
    <header>
      <nav class="navbar">
        <div style="width: 60%">
          <a
            href="./table"
          ><img id="logo" title="Maaf Tidak Ada Akses Keluar" src=../assets/img/back2.png style="margin: 0 8% 0 8%"></a>
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
              <input type="text" class="form-control" id="inputNama">
              <small
                id="inputNama"
                class="form-text text-muted"
              >Setiap kata wajib diawali huruf kapital.</small>
            </div>
            <div class="form-group">
              <label for="inputNIS">NIS Siswa</label>
              <input type="text" class="form-control" id="inputNIS">
            </div>
            <div class="form-group">
              <label for="inputKelas">Kelas Siswa</label>
              <!-- <input type="text" class="form-control" id="inputKelas"> -->
              <select class="form-control" id="inputKelas">
                <option value>Pilih Kelas</option>
                <option value>1</option>
                <option value>2</option>
                <option value>3</option>
                <option value>4</option>
                <option value>5</option>
                <option value>6</option>
              </select>
            </div>
          </form>
          <hr>
          <!-- Trigger -->
          <button type="button" class="btn btn-warning btn-block btn-lg">Tambah Data Siswa</button>
          <hr>
          <a href="./dataSiswa" class="btn btn-success btn-block btn-lg btn-mdf">Lihat Data Siswa</a>
        </div>
        <div class="col align-self-center">
          <form>
            <div class="form-group">
              <label for="inputBuku">Judul Buku</label>
              <input type="text" class="form-control" id="inputBuku">
              <small
                id="inputBuku"
                class="form-text text-muted"
              >Setiap kata wajib diawali huruf kapital.</small>
            </div>
            <div class="form-group">
              <label for="inputKodeBuku">Kode Buku</label>
              <input type="text" class="form-control" id="inputKodeBuku">
            </div>
            <div class="form-group">
              <label for="inputHargaBuku">Harga Buku</label>
              <div class="input-group-prepend">
                <div class="input-group-text">Rp</div>
                <input type="number" class="form-control" id="inputHargaBuku">
              </div>
            </div>
          </form>
          <hr>
          <!-- Trigger -->
          <button type="button" class="btn btn-warning btn-block btn-lg">Tambah Data Buku</button>
          <hr>
          <a href="./dataBuku" class="btn btn-success btn-block btn-lg btn-mdf">Lihat Data Buku</a>
        </div>
        <div class="col align-self-center">
          <button
            type="button"
            class="btn btn-outline-dark btn-block btn-lg disabled"
          >Tahap Pengembangan</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "admin",
  data() {},
  methods: {
    tambahSiswa() {
      // axios.post("http://localhost:3000/api/dataSiswa")
    }
  }
};
</script>

<style>
@import url("../assets/css/bootstrap.min.css");
</style>