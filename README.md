<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TIN NHẮN MẪU</title>

<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#071a2e;
    color:white;
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
}

.container{
    width:90%;
    max-width:900px;
    background:#102844;
    padding:25px;
    border-radius:15px;
    box-shadow:0 0 15px rgba(0,0,0,0.4);
}

h1{
    text-align:center;
    color:#00d4ff;
    margin-bottom:10px;
}

.intro{
    text-align:center;
    color:#d0d0d0;
    margin-bottom:20px;
}

textarea{
    width:100%;
    height:220px;
    border:none;
    border-radius:8px;
    padding:10px;
    font-size:14px;
    resize:vertical;
    box-sizing:border-box;
}

input{
    width:100%;
    padding:10px;
    border:none;
    border-radius:8px;
    margin-top:10px;
    box-sizing:border-box;
}

button{
    width:100%;
    margin-top:15px;
    padding:12px;
    border:none;
    border-radius:8px;
    background:#00bcd4;
    color:white;
    font-size:16px;
    cursor:pointer;
}

button:hover{
    background:#0097a7;
}

.output{
    margin-top:20px;
}

#result{
    height:260px;
    background:#fff;
    color:#000;
}

.footer{
    text-align:center;
    margin-top:20px;
    font-size:12px;
    color:#aaa;
}
</style>
</head>

<body>

<div class="container">

    <h1>TIN NHẮN MẪU</h1>

    <div class="intro">
        Hỗ trợ tạo nội dung từ văn bản giống yêu cầu
    </div>

    <textarea id="inputData" placeholder="Dán dữ liệu khách hàng vào đây..."></textarea>

    <input type="text" id="loanAmount" placeholder="Nhập số tiền vay (VD: 30.000.000)">

    <input type="text" id="bankName" placeholder="Tên ngân hàng / công ty tài chính (VD: SHB)">

    <input type="text" id="contactNumber" placeholder="Số liên hệ bổ sung (VD: 1900 2198)">

    <button onclick="generateMessage()">Tạo Tin Nhắn</button>

    <div class="output">
        <textarea id="result" readonly></textarea>
    </div>

    <div class="footer">
        Since2000
    </div>

</div>

<script>

function getValue(text, key){
    let regex = new RegExp(key + "\\s*:?\\s*(.+)", "i");
    let match = text.match(regex);
    return match ? match[1].trim() : "";
}

function generateMessage(){

    let data = document.getElementById("inputData").value;

    let amount = document.getElementById("loanAmount").value.trim() || "30.000.000";
    let bankName = document.getElementById("bankName").value.trim();
    let contactNumber = document.getElementById("contactNumber").value.trim();

    let name = getValue(data, "Tên KH");
    let cccd = getValue(data, "CCCD");
    let birth = getValue(data, "Ngày Sinh");
    let address = getValue(data, "Địa Chỉ thường trú");

    let bankText = bankName
        ? ` tại công ty tài chính ${bankName}`
        : "";

    let contactText = contactNumber
        ? `${contactNumber} - 0939.965.838`
        : `0939.965.838`;

    let message =
`Đề nghị gia đình báo cho Ông/bà: ${name}
CCCD (CMND) số: ${cccd}
Sinh ngày: ${birth}
Quê quán: ${address}

Liên hệ lại giải quyết khoản vay ${amount} đã quá hạn nghiêm trọng${bankText} để được xem xét miễn giảm lãi phạt trước khi chúng tôi chuyển hồ sơ về Cơ quan có thẩm quyền tại địa phương xử lý theo quy định của Pháp luật. Mọi hậu quả phát sinh ông/bà tự chịu trách nhiệm.

Liên hệ xử lý: ${contactText}`;

    document.getElementById("result").value = message;
}

</script>

</body>
</html>
