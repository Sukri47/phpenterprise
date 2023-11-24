# data_guru -> listpage -> List Page After Record
//status jk
if ($data['jk']== 'Laki - Laki')
$record["jk_css"]='background :lawngreen;';
if ($data['jk']== 'Perempuan')
$record["jk_css"]='background :red;'; 

//stat jurusan
if ($data['jurusan']== 'RPL')
$record["jurusan_css"]='background :lawngreen;';
if ($data['jurusan']== 'OTKP')
$record["jurusan_css"]='background :red;';
if ($data['jurusan']== 'UPW')
$record["jurusan_css"]='background :yellow;';
if ($data['jurusan']== 'AKL')
$record["jurusan_css"]='background :salmon;';

//status guru status_guru
if ($data['status_guru']== 'P3K')
$record["status_guru_css"]='background :orangered;';
if ($data['status_guru']== 'Honor')
$record["status_guru_css"]='background :coral;';
if ($data['status_guru']== 'PNS')
$record["status_guru_css"]='background :aqua;';

# data_izin -> addPage -> Before Record Added
$tgl = date("d");
$tahun = date("Y");
$bulan = date("m");
$datestamp = date("YmdHis", time());
$values["id_code"] = "$datestamp";
$values['add_by'] = $_SESSION["UserID"];
$values['stat_izin'] = "WAITING";

# data_izin -> addPage -> Before Display
$pageObject -> hideField("add_by");
$pageObject -> hideField("update_by");
$pageObject -> hideField("date_update");
$pageObject -> hideField("stat_izin");
$pageObject -> hideField("id_code");

# data_izin -> editPage -> BeforeRecordUpdate
$values['update_by'] =$_SESSION["UserID"];
$values['date_update'] = now();

# data_izin -> editPage -> Before Display
$pageObject -> hideField("add_by");
$pageObject -> hideField("update_by");
$pageObject -> hideField("date_update");

# data_izin -> editPage -> JavaScript On Load Event
var ctrl = Runner.getControl(pageid, 'id_code');
ctrl.setDisabled();

# data_siswa -> List Page -> ListPage After Record
//status jk
if ($data['jenis_kelamin']== 'Laki - Laki')
$record["jenis_kelamin_css"]='background :lawngreen;';
if ($data['jenis_kelamin']== 'Perempuan')
$record["jenis_kelamin_css"]='background :red;'; 

//status agama
if ($data['agama']== 'Islam')
$record["agama_css"]='background :green;';
if ($data['agama']== 'Kristen Protestan')
$record["agama_css"]='background :yellow;';
if ($data['agama']== 'Hindu')
$record["agama_css"]='background : Bisque;';
if ($data['agama']== 'Budha')
$record["agama_css"]='background : pink;';
if ($data['agama']== 'Konghucu')
$record["agama_css"]='background :orange;';

//status kelas
if ($data['kelas']== '1')
$record["kelas_css"]='background :lawngreen;';
if ($data['kelas']== '2')
$record["kelas_css"]='background :red;'; 
if ($data['kelas']== '3')
$record["kelas_css"]='background :lightblue;'; 

# iuran_kelas -> add page -> Before Record Added
$values['add_by'] = $_SESSION["UserID"];

# iuran_kelas -> add page -> before display
$pageObject -> hideField("add_by");
$pageObject -> hideField("update_by");
$pageObject -> hideField("date_update");

# iuran_kelas -> add page -> JavaScript On Load Event
function pajak(){
ctrlPajak.setValue(Number(ctrlBansos.getValue()) * 0.11);
};
ctrlBansos.on('keyup', pajak);
ctrlQuantity.on('keyup', pajak);

//perhitungan total cost
var ctrlTotalCost = Runner.getControl(pageid, 'total_cost');

function totalCost(){
ctrlTotalCost.setValue(Number(ctrlMakanan.getValue()) + Number(ctrlMinuman.getValue()) + Number(ctrlPajak.getValue()));
};

ctrlMakanan.on('keyup', totalCost);
ctrlMinuman.on('keyup', totalCost);
ctrlPajak.on('keyup', totalCost);
ctrlQuantity.on('keyup', totalCost);

//perhitungan pendapatan bersih
var ctrlPendBersih = Runner.getControl(pageid, 'pendapatan_bersih');

function bersih(){
ctrlPendBersih.setValue(Number(ctrlTotal.getValue()) - Number(ctrlTotalCost.getValue()));};

ctrlTotal.on('keyup', bersih);
ctrlTotalCost.on('keyup', bersih);
ctrlQuantity.on('keyup', bersih);

# iuran_kelas -> editpage -> Before Record Update
$values['update_by'] = $_SESSION["UserID"];
$values['date_update'] = now();

# iuran_kelas -> editpage -> Before Display
$pageObject -> hideField("add_by");
$pageObject -> hideField("update_by");
$pageObject -> hideField("date_update");

# iuran_kelas -> editpage -> JavaScript on load event
var ctrlPrice = Runner.getControl(pageid, 'jmlh_byr');
var ctrlQuantity = Runner.getControl(pageid, 'qty');
var ctrlTotal = Runner.getControl(pageid, 'total');

function func() {
ctrlTotal.setValue(Number(ctrlPrice.getValue()) * Number(ctrlQuantity.getValue()));};

ctrlPrice.on('keyup', func);
ctrlQuantity.on('keyup', func);

//perhitungan bansos
ctrlBansos = Runner.getControl(pageid, 'sosial');

function bansos(){
ctrlBansos.setValue(Number(ctrlTotal.getValue()) * 0.5);
};

ctrlTotal.on('keyup' , bansos);
ctrlQuantity.on('keyup' , bansos);

//perhitungan makanan
var ctrlMakanan = Runner.getControl(pageid, 'makanan_sosial');

function makanan(){
ctrlMakanan.setValue(Number(ctrlBansos.getValue()) * 0.7);
};
ctrlBansos.on('keyup', makanan);
ctrlQuantity.on('keyup', makanan);

//perhitungan minuman
var ctrlMinuman = Runner.getControl(pageid, 'minuman_sosial');

function minuman(){
ctrlMinuman.setValue(Number(ctrlBansos.getValue()) * 0.3);
};
ctrlBansos.on('keyup', minuman);
ctrlQuantity.on('keyup', minuman);

//perhitungan ppn
var ctrlPajak = Runner.getControl(pageid, 'ppn_sosial');

function pajak(){
ctrlPajak.setValue(Number(ctrlBansos.getValue()) * 0.11);
};
ctrlBansos.on('keyup', pajak);
ctrlQuantity.on('keyup', pajak);

//perhitungan total cost
var ctrlTotalCost = Runner.getControl(pageid, 'total_cost');

function totalCost(){
ctrlTotalCost.setValue(Number(ctrlMakanan.getValue()) + Number(ctrlMinuman.getValue()) + Number(ctrlPajak.getValue()));
};

ctrlMakanan.on('keyup', totalCost);
ctrlMinuman.on('keyup', totalCost);
ctrlPajak.on('keyup', totalCost);
ctrlQuantity.on('keyup', totalCost);

//perhitungan pendapatan bersih
var ctrlPendBersih = Runner.getControl(pageid, 'pendapatan_bersih');

function bersih(){
ctrlPendBersih.setValue(Number(ctrlTotal.getValue()) - Number(ctrlTotalCost.getValue()));};

ctrlTotal.on('keyup', bersih);
ctrlTotalCost.on('keyup', bersih);
ctrlQuantity.on('keyup', bersih);
