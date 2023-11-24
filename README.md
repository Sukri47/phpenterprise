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
