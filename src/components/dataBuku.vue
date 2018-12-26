<template>
  <div class="DataBuku">
    <header>
      <nav class="navbar">
        <div style="width: 60%">
          <a
            href="./admin"
          ><img id="logo" title="Tombol untuk kembali ke halaman utama" src=../assets/img/back2.png style="margin: 0 15% 0 15%"></a>
          <div class="navbar-brand">Data Buku |</div>
        </div>
        <br>
      </nav>
    </header>
    <br>

    <div class="container">
      <div class="row">
        <div class="form-group col-4">
          <!-- <select class="form-control" v-model="kelas">
            <option value>KELAS</option>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
          </select>-->
        </div>
        <div class="form-group col-4">
          <form>
            <input
              class="form-control"
              type="search"
              aria-label="Search"
              v-model="cari"
              placeholder="Cari Judul Buku"
            >
          </form>
        </div>
        <div class="form-group col-4">
          <a href="./admin" class="btn btn-block btn-warning">Tambah Data Buku</a>
        </div>
      </div>
    </div>

    <div class="container">
      <table class="table table-striped table-bordered table-hover">
        <thead class="thead-dark">
          <tr>
            <th scope="col">Kode Buku</th>
            <th scope="col">Judul Buku</th>
            <th scope="col">Harga Buku</th>
            <th scope="col">Aksi</th>
          </tr>
        </thead>
        <tbody>
          <tr :key="y" v-for="y in cariBuku">
            <td>{{ y.kode_buku }}</td>
            <td>{{ y.nama_buku }}</td>
            <td>{{ y.harga }}</td>
            <td>
              <button
                class="btn btn-outline-success"
                data-toggle="modal"
                data-target="#updateDataBuku"
              >U</button>
              <!-- Modal -->
              <div
                class="modal fade"
                id="updateDataBuku"
                tabindex="-1"
                role="dialog"
                aria-labelledby="exampleModalCenterTitle"
                aria-hidden="true"
              >
                <div class="modal-dialog modal-dialog-centered" role="document">
                  <div class="modal-content">
                    <div class="modal-header">
                      <h5 class="modal-title" id="exampleModalCenterTitle">Update Data Buku</h5>
                      <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                      </button>
                    </div>
                    <div class="modal-body">
                      <div class="form-group">
                        <!-- <label for="exampleInputPassword1">NIS</label> -->
                        <input
                          type="password"
                          class="form-control"
                          id="exampleInputPassword1"
                          placeholder="Kode Buku"
                          disabled
                        >
                      </div>
                      <div class="form-group">
                        <!-- <label for="exampleInputPassword1">Nama</label> -->
                        <input
                          type="password"
                          class="form-control"
                          id="exampleInputPassword1"
                          placeholder="Judul Buku"
                        >
                      </div>
                      <div class="form-group">
                        <!-- <label for="exampleInputPassword1">Kelas</label> -->
                        <input
                          type="password"
                          class="form-control"
                          id="exampleInputPassword1"
                          placeholder="Harga"
                        >
                      </div>
                    </div>
                    <div class="modal-footer">
                      <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                      <button type="button" class="btn btn-primary">Submit</button>
                    </div>
                  </div>
                </div>
              </div>
              <button class="btn btn-outline-danger" @click="deleteBuku(y.kode_buku)">D</button>
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
  name: "DataBuku",
  data() {
    return {
      cari: "",
      buku: []
    };
  },
  methods: {
    deleteBuku(kode_buku) {
      axios
        .delete(`http://localhost:3000/api/buku`, {
          headers: {
            "Content-Type": "application/json"
          },
          data: {
            kode_buku: kode_buku
          }
        })
        .catch(err => {
          console.log(err);
        });
      location.reload();
    }
  },
  created() {
    axios.get("http://localhost:3000/api/buku").then(res => {
      this.buku = res.data;
    });
  },
  computed: {
    cariBuku: function() {
      return this.buku.filter(buku => {
        var ynama = buku.nama_buku.toLowerCase();
        return buku.nama_buku.match(this.cari) || ynama.match(this.cari);
      });
    }
  }
};
</script>

<style>
@import url("../assets/css/bootstrap.min.css");
</style>