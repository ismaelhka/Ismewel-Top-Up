# Ismewel-Top-Up
Página web para recargar UC de PUBG Mobile con PayPal y Banco Pichincha.
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ismewel Top-Up — Recarga UC PUBG Mobile</title>
<style>
:root{
  --primary:#ff6600;
  --bg:#0f0f0f;
  --card-bg:#1e1e1e;
  --text:#ffffff;
  --muted:#cccccc;
  --accent:#ff9900;
}
body{
  margin:0;
  font-family:'Arial',sans-serif;
  background:var(--bg);
  color:var(--text);
}
.wrap{
  max-width:1200px;
  margin:0 auto;
  padding:20px;
}
header{
  display:flex;
  flex-direction:column;
  align-items:center;
  padding-bottom:20px;
  border-bottom:2px solid var(--accent);
}
.logo{
  font-size:28px;
  font-weight:700;
  color:var(--primary);
}
h1{
  font-size:22px;
  margin:6px 0;
}
.lead{
  color:var(--muted);
  text-align:center;
}
.grid{
  display:grid;
  grid-template-columns:3fr 1fr;
  gap:20px;
  margin-top:20px;
}
.catalog{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:20px;
}
.card{
  background:linear-gradient(135deg,#ff6600,#ff9900);
  border-radius:12px;
  overflow:hidden;
  text-align:center;
  box-shadow:0 0 15px rgba(0,0,0,0.5);
  color:#fff;
  position:relative;
  height:160px;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  transition: transform 0.2s;
}
.card:hover{
  transform: scale(1.05);
}
.card h3{
  margin:0;
  font-size:20px;
  font-weight:700;
}
.price{
  color:#fff;
  font-weight:700;
  margin-top:6px;
  font-size:16px;
}
.btn{
  margin-top:8px;
  padding:8px 12px;
  border:none;
  border-radius:8px;
  cursor:pointer;
  font-weight:700;
  color:#fff;
  background:#003087;
}
.btn:disabled{
  background:#555;
  cursor:not-allowed;
}
.sidebar{
  background:var(--card-bg);
  padding:16px;
  border-radius:12px;
  box-shadow:0 0 15px rgba(0,0,0,0.5);
}
.order-form label{
  display:block;
  margin-top:12px;
  color:var(--muted);
}
.order-form input, .order-form select{
  width:100%;
  padding:10px;
  margin-top:6px;
  border-radius:8px;
  border:none;
  background:#2a2a2a;
  color:#fff;
}
.order-summary{
  margin-top:12px;
  padding:12px;
  border:1px dashed var(--accent);
  border-radius:8px;
  color:var(--muted);
}
.feedback{
  margin-top:12px;
  padding:12px;
  border-radius:8px;
  background:#003087;
  color:#fff;
  display:none;
  text-align:center;
}
footer{
  text-align:center;
  padding:12px;
  margin-top:20px;
  border-top:1px solid var(--accent);
  color:var(--muted);
}
@media(max-width:900px){
  .grid{grid-template-columns:1fr;}
}
</style>
</head>
<body>
<div class="wrap">
<header>
  <div class="logo">Ismewel Top-Up</div>
  <h1>Recarga UC PUBG Mobile</h1>
  <p class="lead">Usuarios de Ecuador pueden pagar por Banco Pichincha. Otros países deben usar PayPal. Confirmamos la recarga tras verificar el pago.</p>
</header>

<div class="grid">
  <div class="catalog">
    <div class="card" data-uc="60" data-price="0.99">
      <h3>60 UC</h3>
      <div class="price">Precio final: $<span class="final"></span></div>
      <button class="btn select-btn" data-uc="60" data-price="0.99">Seleccionar</button>
    </div>
    <div class="card" data-uc="300" data-price="4.99">
      <h3>300 UC</h3>
      <div class="price">Precio final: $<span class="final"></span></div>
      <button class="btn select-btn" data-uc="300" data-price="4.99">Seleccionar</button>
    </div>
    <div class="card" data-uc="680" data-price="9.99">
      <h3>680 UC</h3>
      <div class="price">Precio final: $<span class="final"></span></div>
      <button class="btn select-btn" data-uc="680" data-price="9.99">Seleccionar</button>
    </div>
    <div class="card" data-uc="1320" data-price="19.99">
      <h3>1320 UC</h3>
      <div class="price">Precio final: $<span class="final"></span></div>
      <button class="btn select-btn" data-uc="1320" data-price="19.99">Seleccionar</button>
    </div>
    <div class="card" data-uc="2640" data-price="49.99">
      <h3>2640 UC</h3>
      <div class="price">Precio final: $<span class="final"></span></div>
      <button class="btn select-btn" data-uc="2640" data-price="49.99">Seleccionar</button>
    </div>
    <div class="card" data-uc="8100" data-price="99.99">
      <h3>8100 UC</h3>
      <div class="price">Precio final: $<span class="final"></span></div>
      <button class="btn select-btn" data-uc="8100" data-price="99.99">Seleccionar</button>
    </div>
  </div>

  <div class="sidebar">
    <form class="order-form" id="orderForm">
      <label>Nick PUBG</label>
      <input type="text" id="nick" required placeholder="Tu Nick PUBG">

      <label>Plataforma</label>
      <select id="platform" required>
        <option value="Android">Android</option>
        <option value="iOS">iOS</option>
      </select>

      <label>Paquete seleccionado</label>
      <input type="text" id="pack" readonly required placeholder="Selecciona un paquete">

      <label>Precio final (USD)</label>
      <input type="text" id="price" readonly required placeholder="$0.00">

      <label>País de residencia</label>
      <input type="text" id="country" required placeholder="Ej: Ecuador">

      <label>Método de pago</label>
      <select id="method" required>
        <option value="paypal">PayPal (otros países)</option>
        <option value="bank">Banco Pichincha (solo Ecuador)</option>
      </select>

      <div class="order-summary">
        <div>Banco Pichincha (solo para usuarios de Ecuador)</div>
        <div>Cuenta de ahorro: 2212896512</div>
        <div>PayPal (otros países): <a href="https://www.paypal.me/Ismewel" target="_blank" style="color:var(--accent)">paypal.me/Ismewel</a></div>
        <small>Después de pagar, envía el comprobante a <strong>quinteroismael38@gmail.com</strong> incluyendo tu nick y país de residencia.</small>
      </div>

      <button class="btn" type="submit" style="width:100%;margin-top:12px;">Notificar pago</button>
      <div class="feedback" id="feedback">¡Orden lista! Revisa tu correo para enviar el comprobante.</div>
    </form>
  </div>
</div>

<footer>
  © Ismewel Top-Up — Recargas oficiales mediante Midasbuy / canales autorizados.
</footer>
</div>

<script>
// Calcular precio final
document.querySelectorAll('.card').forEach(card=>{
  const officialPrice = parseFloat(card.dataset.price);
  const final = (officialPrice + 4).toFixed(2);
  card.querySelector('.final').textContent = final;
});

// Seleccionar paquete
document.querySelectorAll('.select-btn').forEach(btn=>{
  btn.addEventListener('click',()=>{
    const uc = btn.dataset.uc;
    const officialPrice = parseFloat(btn.dataset.price);
    const final = (officialPrice + 4).toFixed(2);
    document.getElementById('pack').value = uc + ' UC';
    document.getElementById('price').value = '$' + final;
    document.getElementById('nick').scrollIntoView({behavior:'smooth'});

    // Resaltar tarjeta seleccionada
    document.querySelectorAll('.card').forEach(c=>c.style.border="none");
    btn.parentElement.style.border = `3px solid var(--accent)`;
  });
});

// Enviar orden por mail
document.getElementById('orderForm').addEventListener('submit', function(e){
  e.preventDefault();
  const nick = document.getElementById('nick').value.trim();
  const platform = document.getElementById('platform').value;
  const pack = document.getElementById('pack').value;
  const price = document.getElementById('price').value;
  const country = document.getElementById('country').value.trim().toLowerCase();
  const method = document.getElementById('method').value;

  // Validación
  if(!nick || !platform || !pack || !price || !country || !method){
    alert('Por favor completa todos los campos.');
    return false;
  }
  if(country !== 'ecuador' && method==='bank'){
    alert('Solo usuarios de Ecuador pueden pagar por Banco Pichincha. Otros países deben usar PayPal.');
    return false;
  }

  const subject = encodeURIComponent('Nueva orden UC - '+pack+' - '+nick);
  const body = encodeURIComponent(
    'Nueva orden desde la web\n\nNick: '+nick+
    '\nPlataforma: '+platform+
    '\nPaquete: '+pack+
    '\nPrecio: '+price+
    '\nPaís de residencia: '+country+
    '\nMétodo: '+(method==='paypal'?'PayPal (paypal.me/Ismewel)':'Depósito Banco Pichincha 2212896512 (Cuenta de ahorro)')+
    '\n\nEnvía el comprobante a quinteroismael38@gmail.com incluyendo tu nick y país de residencia.'
  );

  // Abrir cliente de correo
  window.location.href='mailto:quinteroismael38@gmail.com?subject='+subject+'&body='+body;

  // Feedback visual
  const feedback = document.getElementById('feedback');
  feedback.style.display = 'block';
  feedback.scrollIntoView({behavior:'smooth'});
});
</script>
</body>
</html>
