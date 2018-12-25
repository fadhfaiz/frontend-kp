<template>
    <div class = "buku">
        <header>
		<nav class="navbar">
			<div style="width: 60%">
				<a href="./">
					<img id="logo" title="tombol untuk kembali ke halaman utama" src=../assets/img/back2.png style="margin: 0 15% 0 15%">
				</a>
				<div class="navbar-brand">Menu Pembelian Buku |</div>
			</div>
			<br>
			<button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
			    aria-expanded="false" aria-label="Toggle navigation">
				<span class="navbar-toggler-icon"></span>
			</button>
		</nav>
	</header>
	<div class="container" id="app">
		<br>
		<nav class="row col-md-12">
			<div class="col-md-4">
				<div class="form-group">
					<select class="form-control" v-model="kelas">
						<option value="">KELAS</option>
						<option value="1">KELAS 1</option>
						<option value="2">KELAS 2</option>
						<option value="3">KELAS 3</option>
						<option value="4">KELAS 4</option>
						<option value="5">KELAS 5</option>
						<option value="6">KELAS 6</option>
					</select>
				</div>
			</div>
			<div class="form-group col-md-4">
				<form>
					<input class="form-control" type="search" placeholder="Cari Nama / NIS . . ." aria-label="Search" v-model = "cari">
					<!-- <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button> -->
				</form>
			</div>
			<div class="col-md-4">
				<button class="btn btn-warning btn-block" @click="simpan()"> Simpan Data </button>
			</div>
		</nav>
		<br>

		<table class="table table-striped table-bordered table-hover">
			<thead class="thead-dark">
				<tr>
					<th scope="col" align="center" style="padding-bottom: 40px " rowspan="2">NIS</th>
					<th scope="col" align="center" style="padding-bottom: 40px " rowspan="2">NAMA</th>
					<th v-for="xy in daftar" :key="xy" scope="col" align="center" style="padding-bottom: 40px">
						{{xy.nama_buku}}
					</th>
					<!-- <th scope="col">Buku A</th>
					<th scope="col">Buku B</th>
					<th scope="col">Buku C</th>
					<th scope="col">Buku D</th> -->
				</tr>
				<!-- <tr>
					<td v-for="oko in siswa" :key="oko">
						{{oko.nis}}
					</td>
					<td v-for="maya in siswa" :key="maya">
						{{maya.nama}}
					</td>
				</tr> -->
			</thead>
			<tbody>
				<tr :key="x" v-for="x in cariData" v-if="x.kelas == kelas || kelas == ''">
					<td>{{ x.nis }} </td>
					<td>{{ x.nama_siswa | capitalize}}</td>
					<td>
						<input type="checkbox" v-model="x.buku1" v-if="!x.ambil1"> 
					</td>
					<td>
						<input type="checkbox" v-model="x.buku2" v-if="!x.ambil2"> 
					</td>
					<td>
						<input type="checkbox" v-model="x.buku3" v-if="!x.ambil3"> </td>
					<!-- <td> -->
						<!-- <input type="checkbox" v-model="x.buku4" v-if="!x.ambil4"> </td> -->
				</tr>

			</tbody>
		</table>

		<br>

	</div>
    </div>
</template>

<script>
	import swal from 'sweetalert'
	import axios from 'axios'
    export default{
		name: 'buku',
		data() {
			return {
				kelas: '',
				cari: '',
				tagihansemester: 250000, 
				tagihanbulan: 50000,
				// i: 1,
				total: 0,
				totalSiswa: 0,
				siswa:[
					// {'no': 1, 'nis': '1234', 'nama': 'maya', 'kelas': '3', 'bayar': 10000, 'totalbayar': 10000, 'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0, 'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 2, 'nis': '2131', 'nama': 'faiz', 'kelas': '1', 'bayar': 20000, 'totalbayar': 20000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0 },
					// {'no': 3, 'nis': '7873', 'nama': 'qori', 'kelas': '4', 'bayar': 30000, 'totalbayar': 30000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 4, 'nis': '5473', 'nama': 'aulia', 'kelas': '5', 'bayar': 40000, 'totalbayar': 40000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 5, 'nis': '0982', 'nama': 'robin', 'kelas': '6', 'bayar': 50000, 'totalbayar': 50000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 6, 'nis': '5621', 'nama': 'helty', 'kelas': '2', 'bayar': 6000, 'totalbayar': 6000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 7, 'nis': '7861', 'nama': 'shofi', 'kelas': '1', 'bayar': 7000, 'totalbayar': 7000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 8, 'nis': '1562', 'nama': 'dila', 'kelas': '3', 'bayar': 8000, 'totalbayar': 8000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 9, 'nis': '5617', 'nama': 'insan', 'kelas': '6', 'bayar': 9000, 'totalbayar': 9000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 10, 'nis': '9378', 'nama': 'rebecca', 'kelas': '4', 'bayar': 10000, 'totalbayar': 10000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},
					// {'no': 11, 'nis': '1564', 'nama': 'hery', 'kelas': '5', 'bayar': 11000, 'totalbayar': 11000,'buku1': 0, 'ambil1': 0, 'buku2': 0, 'ambil2': 0, 'buku3': 0,'ambil3': 0, 'buku4': 0, 'ambil4': 0},

				],
				daftar: []
		}
	},

	filters: {
		capitalize: function(value) {
			if(!value) return ''
			value = value.toString()
			return value.charAt(0).toUpperCase() + value.slice(1)
		}
	},

	created(){
		axios.get("http://localhost:3000/api/buku").then((res)=> {
			this.daftar = res.data;
			console.log(res.data)
		})

		axios.get("http://localhost:3000/api/dataSiswa").then((res)=> {
			this.siswa = res.data;
			console.log(res.data)
		})


		for(var i = 0; i < this.siswa.length; i++){
			this.total += this.siswa[i].jumlah
		}

		this.totalSiswa = this.siswa.length
	},
	methods: {
		simpan() {
			var test = [];

			this.siswa.forEach(dt => {
				dt.ambil1 = dt.buku1
				dt.ambil2 = dt.buku2
				dt.ambil3 = dt.buku3
				dt.ambil4 = dt.buku4

				test.push({
					nis: dt.nis,
					buku1: dt.buku1,
					buku2: dt.buku2,
					buku3: dt.buku3,
					buku4: dt.buku4,
				})
			})
			
			swal('Terimakasih', 'Data Berhasil Disimpan', 'success')
			// alert(`${test[0].nis} - ${test[0].buku2}`)
		}
	},
	computed: {
		cariData: function(){
			return this.siswa.filter((siswa) => {
				var xnama = siswa.nama_siswa.charAt(0).toUpperCase() + siswa.nama_siswa.slice(1);
				return siswa.nis.match(this.cari) || siswa.nama_siswa.match(this.cari) || xnama.match(this.cari);
			});
		}
	}
    }
</script>

<style>
    @import url('../assets/css/bootstrap.min.css');
</style>
