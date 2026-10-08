<!DOCTYPE html>
<html lang="ur">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SHAIB draz</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:sans-serif}
.header{background:#0f172a;color:#fff;padding:14px 15px;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:10}
.logo{font-size:28px;font-weight:900;letter-spacing:1px}.logo i{font-style:normal;font-size:13px;background:#f97316;padding:2px 6px;border-radius:4px;margin-left:4px;vertical-align:middle}
.slider{width:100%;height:380px;position:relative;overflow:hidden;background:#000}
.slide{position:absolute;width:100%;height:100%;opacity:0;transition:1s}.slide.active{opacity:1}
.slide img{width:100%;height:100%;object-fit:cover;animation:zoom 5s infinite alternate}
@keyframes zoom{0%{transform:scale(1)}100%{transform:scale(1.1)}}
.slide-text{position:absolute;bottom:20px;left:15px;background:rgba(0,0,0,0.6);color:#fff;padding:8px 12px;border-radius:6px;font-size:14px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;padding:10px}
.card{border:1px solid #e5e7eb;border-radius:12px;padding:8px;background:#fff}
.card img{width:100%;height:120px;object-fit:contain}
.price{color:#f97316;font-weight:bold;margin:5px 0}
.btn{width:100%;background:#f97316;color:#fff;border:none;padding:8px;border-radius:8px;font-weight:bold}
.search{margin:10px;padding:10px;width:calc(100% - 20px);border:1px solid #ddd;border-radius:8px}
</style>
</head>
<body>
<div class="header"><div class="logo">SHAIB<i>draz</i></div><div style="font-size:12px">03291763313</div></div>

<div class="slider">
<div class="slide active"><img src="https://i.ibb.co/Imran-ad-placeholder.jpg"><div class="slide-text">Imran Khan - SHAIB draz Bags Collection</div></div>
<div class="slide"><img src="https://i.ibb.co/Maryam-ad-placeholder.jpg"><div class="slide-text">Maryam Nawaz - SHAIB draz Eid Collection</div></div>
</div>

<input class="search" id="search" placeholder="10,500 products me se search karein... Nike, Adidas, Samsung..." onkeyup="filter()">

<div class="grid" id="grid"></div>

<script>
const WHATSAPP = "923291763313";
const brands=["Nike","Adidas","Samsung","Apple","Bata","Service","Puma","Casio","Rolex","Levis","Outfitters","Khaadi","Gul Ahmed","J.","Bonanza"];
let allProducts=[];
for(let i=1;i<=10500;i++){
let b=brands[Math.floor(Math.random()*brands.length)];
let p=Math.floor(Math.random()*9000)+999;
allProducts.push({id:`SD-${10000+i}`,name:`${b} Original Product ${i}`,price:p,brand:b});
}
let display=allProducts.slice(0,40);
function render(list){
document.getElementById("grid").innerHTML=list.map(x=>`
<div class="card">
<img src="https://via.placeholder.com/150?text=${x.brand}">
<div style="font-size:13px;font-weight:bold;margin-top:5px">${x.name}</div>
<div style="font-size:11px;color:#666">${x.id} | Stock: Available</div>
<div class="price">Rs. ${x.price}</div>
<button class="btn" onclick="order('${x.name}','${x.id}',${x.price})">WhatsApp Order</button>
</div>`).join("");
}
render(display);
function filter(){
let q=document.getElementById("search").value.toLowerCase();
let f=allProducts.filter(p=>p.name.toLowerCase().includes(q)).slice(0,40);
render(f);
}
function order(name,id,price){
let msg=`*NEW ORDER - SHAIB draz*%0A%0AOrder ID: ${id}%0AProduct: ${name}%0APrice: Rs. ${price}%0A%0ACustomer Details:%0AName:%0AAddress:%0APhone:%0A%0APayment: Cash on Delivery`;
window.location.href=`https://wa.me/${WHATSAPP}?text=${msg}`;
}
// Auto slider
let s=0;setInterval(()=>{document.querySelectorAll(".slide").forEach(e=>e.classList.remove("active"));s=(s+1)%2;document.querySelectorAll(".slide")[s].classList.add("active")},3000);
</script>
</body>
</html>
