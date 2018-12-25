<template>
  <div class="DataSiswa">
    <header>
      <nav class="navbar">
        <div style="width: 60%">
          <a
            href="./admin"
          ><img id="logo" title="Tombol untuk kembali ke halaman utama" src=../assets/img/back2.png style="margin: 0 15% 0 15%"></a>
          <div class="navbar-brand">Data Siswa |</div>
        </div>
        <br>
      </nav>
    </header>
    <br>

    <div class="container">
      <div class="row">
        <div class="form-group col-4">
          <select class="form-control" v-model="kelas">
            <option value>KELAS</option>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
          </select>
        </div>
        <div class="form-group col-4">
          <form>
            <input
              class="form-control"
              type="search"
              aria-label="Search"
              v-model="cari"
              placeholder="Cari Nama / NIS"
            >
          </form>
        </div>
        <div class="form-group col-4">
          <a href="./admin" class="btn btn-block btn-warning">Tambah Data Siswa</a>
        </div>
      </div>
    </div>

    <div class="container">
      <table class="table table-striped table-bordered table-hover">
        <thead class="thead-dark">
          <tr>
            <!-- <th scope="col">No</th> -->
            <th scope="col">NIS</th>
            <th scope="col">Nama</th>
            <th scope="col">Kelas</th>
            <th scope="col">Aksi</th>
          </tr>
        </thead>
        <tbody>
          <tr :key="x" v-for="x in cariData" v-if="x.kelas == kelas || kelas == ''">
            <td>{{ x.nis }}</td>
            <td>{{ x.nama_siswa}}</td>
            <td>{{ x.kelas }}</td>
            <td>
              <button class="btn btn-outline-success">U</button>
              <button class="btn btn-outline-danger">D</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "DataSiswa",
  data() {
    return {
      siswa: [],
      kelas: "",
      cari: ""
    };
  },
  created() {
    axios.get("http://localhost:3000/api/dataSiswa").then(res => {
      this.siswa = res.data;
      console.log(res.data);
    });
  },
  computed: {
    cariData: function() {
      return this.siswa.filter(siswa => {
        // var xnama = siswa.nama_siswa.charAt(0).toUpperCase() + siswa.nama_siswa.slice(1);
        var xnama = siswa.nama_siswa.toLowerCase();
        return (
          siswa.nis.match(this.cari) ||
          siswa.nama_siswa.match(this.cari) ||
          xnama.match(this.cari)
        );
      });
    }
  }
};
</script>

<style>
@import url("../assets/css/bootstrap.min.css");
</style>