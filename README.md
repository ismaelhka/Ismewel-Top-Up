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
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:15px;margin-top:15px;}
.card{background:var(--card-bg);border-radius:12px;padding:20px;text-align:center;box-shadow:0 3px 8px rgba(0,0,0,0.15);cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;}
.card:hover{transform:translateY(-5px);box-shadow:0 8px 20px rgba(0,0,0,0.3);}
.card h3{margin:0;color:var(--primary);}
.card p{margin:8px 0 0;font-weight:700;color:var(--accent);}
.payment-methods{display:none;margin-top:15px;}
.payment-method{padding:10px;border:1px solid #ddd;border-radius:8px;margin-top:8px;background:#fafafa;}
footer{text-align:center;margin-top:40px;padding:15px;color:var(--muted);font-size:13px;}
.verified{color:#009900;font-weight:700;font-size:14px;margin-bottom:10px;}
.btn{margin-top:12px;background:var(--btn);color:#fff;padding:10px 14px;border:none;border-radius:8px;cursor:pointer;font-weight:600;transition:background .2s;width:100%;}
.btn:hover{background:#002060;}
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
<label>ID del jugador</label>
<input type="text" id="uid" required placeholder="Ej: 123456789">

<label>Plataforma</label>
<select id="platform" required>
<option value="">Selecciona plataforma</option>
<option value="Android">Android</option>
<option value="iOS">iOS</option>
</select>

<label>Paquete UC</label>
<div class="cards">
  <div class="card" data-uc="60" data-price="1.00">
    <h3>60 UC</h3><p>$1.00</p>
  </div>
  <div class="card" data-uc="300" data-price="6.99">
    <h3>300 UC</h3><p>$6.99</p>
  </div>
  <div class="card" data-uc="680" data-price="13.99">
    <h3>680 UC</h3><p>$13.99</p>
  </div>
  <div class="card" data-uc="1320" data-price="23.99">
    <h3>1320 UC</h3><p>$23.99</p>
  </div>
  <div class="card" data-uc="2640" data-price="53.99">
    <h3>2640 UC</h3><p>$53.99</p>
  </div>
  <div class="card" data-uc="8100" data-price="103.99">
    <h3>8100 UC</h3><p>$103.99</p>
  </div>
</div>

<label>Precio final (USD)</label>
<input type="text" id="price" readonly placeholder="$0.00">

<label>País</label>
<select id="country" required>
  <option value="">Selecciona tu país</option>
  <option value="Ecuador">Ecuador</option>
  <option value="Argentina">Argentina</option>
  <option value="Brasil">Brasil</option>
  <option value="Chile">Chile</option>
  <option value="Colombia">Colombia</option>
  <option value="México">México</option>
  <option value="Perú">Perú</option>
  <option value="España">España</option>
  <option value="Estados Unidos">Estados Unidos</option>
  <option value="Venezuela">Venezuela</option>
  <option value="Uruguay">Uruguay</option>
  <option value="Paraguay">Paraguay</option>
  <option value="Bolivia">Bolivia</option>
</select>

<div class="payment-methods" id="payment-methods">
  <div class="payment-method" id="paypal-method">
    🌐 <strong>Pagar con PayPal o tarjeta de débito:</strong>
    <div id="paypal-buttons"></div>
  </div>
  <div class="payment-method" id="bank-method">
    💳 Banco Pichincha (solo Ecuador): <strong>2212896512</strong>
  </div>
</div>

<button class="btn" type="submit">Enviar pedido por correo</button>
</form>
</main>

<footer>© 2025 Recargas oficiales — Todos los derechos reservados</footer>

<script>
document.addEventListener('DOMContentLoaded', () => {
  const cards = document.querySelectorAll('.card');
  const priceInput = document.getElementById('price');
  const paymentMethods = document.getElementById('payment-methods');
  const paypalButtonsContainer = document.getElementById('paypal-buttons');
  let selectedPrice = 0;

  function renderPayPalButton(amount){
    paypalButtonsContainer.innerHTML = ''; // limpia si hay botón previo
    if(amount <= 0) return;

    // Botón clásico HTML de PayPal
    const form = document.createElement('form');
    form.action = "https://www.paypal.com/cgi-bin/webscr";
    form.method = "post";
    form.target = "_blank";

    form.innerHTML = `
      <input type="hidden" name="cmd" value="_xclick">
      <input type="hidden" name="business" value="S29ADWZU8J9GY">
      <input type="hidden" name="item_name" value="Recarga UC PUBG Mobile">
      <input type="hidden" name="amount" value="${amount.toFixed(2)}">
      <input type="hidden" name="currency_code" value="USD">
      <input type="hidden" name="no_shipping" value="1">
      <input type="submit" value="Pagar $${amount.toFixed(2)} con PayPal" class="btn">
    `;

    paypalButtonsContainer.appendChild(form);
  }

  cards.forEach(card => {
    card.addEventListener('click', () => {
      cards.forEach(c => c.style.border = "none");
      card.style.border = "2px solid var(--primary)";
      selectedPrice = parseFloat(card.dataset.price);
      priceInput.value = `$${selectedPrice.toFixed(2)}`;
      paymentMethods.style.display = 'block';
      renderPayPalButton(selectedPrice);
    });
  });

  document.getElementById('order-form').addEventListener('submit', e => {
    e.preventDefault();
    const uid = document.getElementById('uid').value.trim();
    const platform = document.getElementById('platform').value;
    const price = priceInput.value;
    const country = document.getElementById('country').value;

    if(!/^\d{5,20}$/.test(uid)){
      alert('Ingresa un ID válido (solo números).');
      return;
    }

    const mailto = `mailto:aroontigre@gmail.com?subject=Pedido UC PUBG (${uid})&body=ID del jugador: ${uid}%0APlataforma: ${platform}%0APaís: ${country}%0APrecio: ${price}`;
    window.location.href = mailto;
  });
});
</script>
</body>
</html>
