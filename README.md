# Ismewel-Top-Up
Página web para recargar UC de PUBG Mobile con PayPal y Banco Pichincha.
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Recargas oficiales — UC PUBG Mobile</title>
<style>
:root {
  --primary:#ff6600;
  --accent:#ff9900;
  --bg:#fdfdfd;
  --card-bg:#ffffff;
  --text:#111;
  --muted:#555;
  --btn:#003087;
}
*{box-sizing:border-box;}
body{margin:0;font-family:'Poppins',sans-serif;background:var(--bg);color:var(--text);}
header{padding:25px 10px;text-align:center;border-bottom:2px solid var(--accent);}
header h1{font-size:28px;margin:0;color:var(--primary);}
header p{margin:5px 0 0;color:var(--muted);}
main{max-width:1000px;margin:30px auto;padding:0 20px;}
label{display:block;margin-top:10px;font-size:14px;color:var(--muted);}
input,select{width:100%;margin-top:5px;padding:10px;border-radius:6px;border:1px solid #ddd;background:#fff;color:#111;}
input[type="text"]#country{padding-right:35px;}
.btn{margin-top:12px;background:var(--btn);color:#fff;padding:10px 14px;border:none;border-radius:8px;cursor:pointer;font-weight:600;transition:background .2s;width:100%;}
.btn:hover{background:#002060;}
.order-summary{margin-top:15px;padding:10px;border:1px dashed var(--accent);border-radius:8px;font-size:13px;color:var(--muted);}
footer{text-align:center;padding:20px;margin-top:40px;border-top:1px solid var(--accent);font-size:13px;color:var(--muted);}
.verified{color:#009900;font-weight:700;font-size:14px;margin-bottom:10px;}
.search-container{position:relative;}
.search-container input{width:100%;padding-right:35px;}
.search-container button{
  position:absolute;right:5px;top:50%;transform:translateY(-50%);
  border:none;background:transparent;cursor:pointer;font-size:18px;color:var(--accent);
}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:15px;margin-top:15px;}
.card{background:var(--card-bg);border-radius:12px;padding:20px;text-align:center;box-shadow:0 3px 8px rgba(0,0,0,0.15);cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;}
.card:hover{transform:translateY(-5px);box-shadow:0 8px 20px rgba(0,0,0,0.3);}
.card h3{margin:0;color:var(--primary);}
.card p{margin:8px 0 0;font-weight:700;color:var(--accent);}
</style>
</head>
<body>
<header>
  <h1>Recargas oficiales</h1>
  <p class="verified">✅ Sitio verificado y seguro</p>
  <p>Recarga UC de PUBG Mobile con PayPal o Banco Pichincha</p>
</header>

<main>
<form id="order-form">
<label>Nick de PUBG</label>
<input type="text" id="nick" required placeholder="Tu nombre en el juego">

<label>Plataforma</label>
<select id="platform" required>
<option value="">Selecciona plataforma</option>
<option value="Android">Android</option>
<option value="iOS">iOS</option>
</select>

<label>Paquete UC</label>
<div class="cards">
  <div class="card" data-uc="60" data-price="1">
    <h3>60 UC</h3>
    <p>$1.00</p>
  </div>
  <div class="card" data-uc="300" data-price="6.99">
    <h3>300 UC</h3>
    <p>$6.99</p>
  </div>
  <div class="card" data-uc="680" data-price="13.99">
    <h3>680 UC</h3>
    <p>$13.99</p>
  </div>
  <div class="card" data-uc="1320" data-price="23.99">
    <h3>1320 UC</h3>
    <p>$23.99</p>
  </div>
  <div class="card" data-uc="2640" data-price="53.99">
    <h3>2640 UC</h3>
    <p>$53.99</p>
  </div>
  <div class="card" data-uc="8100" data-price="103.99">
    <h3>8100 UC</h3>
    <p>$103.99</p>
  </div>
</div>

<label>Precio final (USD)</label>
<input type="text" id="price" readonly placeholder="$0.00">

<label>País</label>
<div class="search-container">
  <input list="countries" id="country" placeholder="Escribe tu país" required>
  <button type="button">🔍</button>
</div>
<datalist id="countries">
<option value="Ecuador">
<option value="Argentina">
<option value="Brasil">
<option value="Chile">
<option value="Colombia">
<option value="México">
<option value="Perú">
<option value="España">
<option value="Estados Unidos">
<option value="Venezuela">
<!-- Puedes agregar todos los países -->
</datalist>

<label>Método de pago</label>
<select id="method" required>
<option value="">Selecciona método</option>
<option value="paypal">PayPal / Tarjeta de débito o crédito</option>
<option value="bank">Banco Pichincha (solo Ecuador)</option>
</select>

<div class="order-summary">
<p>💳 Banco Pichincha (solo Ecuador): <strong>2212896512</strong></p>
<p>🌐 PayPal / Tarjeta: <a id="paypal-link" href="https://www.paypal.me/ismaelquintero2018/1" target="_blank" style="color:var(--accent)">Pagar con PayPal</a></p>
<small>Tras pagar, envía el comprobante a <strong>ismaelquintero2018@gmail.com</strong> con tu nick y país.</small>
</div>

<button class="btn" type="submit">Enviar pedido por correo</button>
</form>
</main>

<footer>© 2025 Recargas oficiales — Todos los derechos reservados</footer>

<script>
// Selección de paquete con tarjetas
const cards = document.querySelectorAll('.card');
const priceInput = document.getElementById('price');
const paypalLink = document.getElementById('paypal-link');

cards.forEach(card=>{
  card.addEventListener('click',()=>{
    cards.forEach(c=>c.style.border="none");
    card.style.border="2px solid var(--primary)";
    const price = card.dataset.price;
    const uc = card.dataset.uc;
    priceInput.value = `$${price}`;
    paypalLink.href = `https://www.paypal.me/ismaelquintero2018/${price}`;
  });
});

// Enviar formulario por mail
document.getElementById('order-form').addEventListener('submit', e=>{
  e.preventDefault();
  const nick = document.getElementById('nick').value;
  const platform = document.getElementById('platform').value;
  const uc = document.querySelector('.card[style*="border"]')?.dataset.uc || '';
  const price = priceInput.value;
  const country = document.getElementById('country').value;
  const method = document.getElementById('method').value;
  const subject = encodeURIComponent(`Nueva orden UC - ${uc} UC - ${nick}`);
  const body = encodeURIComponent(
`Orden de recarga:\n\nNick: ${nick}\nPlataforma: ${platform}\nPaquete: ${uc} UC\nPrecio: ${price}\nPaís: ${country}\nMétodo: ${method}\n\nEnviar comprobante a ismaelquintero2018@gmail.com`
  );
  window.location.href = `mailto:ismaelquintero2018@gmail.com?subject=${subject}&body=${body}`;
});
</script>
</body>
</html>
