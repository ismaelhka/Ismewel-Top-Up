<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
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
.btn{margin-top:12px;background:var(--btn);color:#fff;padding:10px 14px;border:none;border-radius:8px;cursor:pointer;font-weight:600;transition:background .2s;width:100%;}
.btn:hover{background:#002060;}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:15px;margin-top:15px;}
.card{background:var(--card-bg);border-radius:12px;padding:20px;text-align:center;box-shadow:0 3px 8px rgba(0,0,0,0.15);cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;border:1px solid transparent;}
.card:hover{transform:translateY(-5px);box-shadow:0 8px 20px rgba(0,0,0,0.3);}
.card.active{border-color:var(--primary);box-shadow:0 10px 25px rgba(0,0,0,0.18);}
.card h3{margin:0;color:var(--primary);}
.card p{margin:8px 0 0;font-weight:700;color:var(--accent);}
.payment-methods{display:none;margin-top:15px;}
.payment-method{padding:10px;border:1px solid #ddd;border-radius:8px;margin-top:8px;background:#fafafa;}
.payment-method strong{color:var(--primary);}
.verified{color:#009900;font-weight:700;font-size:14px;margin-bottom:10px;}
footer{text-align:center;margin-top:40px;padding:15px;color:var(--muted);font-size:13px;}
small{color:var(--muted);}
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
<small>El ID lo encuentras en tu perfil del juego (solo números)</small>

<label>Plataforma</label>
<select id="platform" required>
  <option value="">Selecciona plataforma</option>
  <option value="Android">Android</option>
  <option value="iOS">iOS</option>
</select>

<label>Paquete UC</label>
<div class="cards">
  <div class="card" data-uc="60" data-price="1.00"><h3>60 UC</h3><p>$1.00</p></div>
  <div class="card" data-uc="300" data-price="6.99"><h3>300 UC</h3><p>$6.99</p></div>
  <div class="card" data-uc="680" data-price="13.99"><h3>680 UC</h3><p>$13.99</p></div>
  <div class="card" data-uc="1320" data-price="23.99"><h3>1320 UC</h3><p>$23.99</p></div>
  <div class="card" data-uc="2640" data-price="53.99"><h3>2640 UC</h3><p>$53.99</p></div>
  <div class="card" data-uc="8100" data-price="103.99"><h3>8100 UC</h3><p>$103.99</p></div>
</div>

<label>Precio final (USD)</label>
<input type="text" id="price" readonly placeholder="$0.00">

<label>País</label>
<select id="country" required>
  <option value="">Selecciona tu país</option>
  <option>Ecuador</option><option>Argentina</option><option>Brasil</option>
  <option>Chile</option><option>Colombia</option><option>México</option>
  <option>Perú</option><option>España</option><option>Estados Unidos</option>
  <option>Venezuela</option><option>Uruguay</option><option>Paraguay</option><option>Bolivia</option>
</select>

<div class="payment-methods" id="payment-methods">
  <div class="payment-method">
    🌐 <strong>Pagar con PayPal o tarjeta de débito:</strong>
    <div id="paypal-button-container" style="margin-top:10px;"></div>
    <p><small>Si no se carga el botón, usa el enlace directo: <a id="paypalme" href="#" target="_blank">paypal.me/tuusuario</a></small></p>
  </div>
  <div class="payment-method">
    💳 Banco Pichincha (solo Ecuador): <strong>2212896512</strong>
  </div>
</div>

<button class="btn" type="submit">Enviar pedido por correo</button>
</form>
</main>

<footer>© 2025 Recargas oficiales — Todos los derechos reservados</footer>

<script>
const PAYPAL_CLIENT_ID = "S29ADWZU8J9GY"; // ✅ tu Client ID real
const PAYPALME_USER = "tuusuario"; // Cambia por tu enlace paypal.me/usuario

let selectedPrice = 0;

// Cargar SDK de PayPal
function loadPayPalSDK() {
  return new Promise((resolve, reject) => {
    if (window.paypal) return resolve(window.paypal);
    const script = document.createElement("script");
    script.src = `https://www.paypal.com/sdk/js?client-id=${encodeURIComponent(PAYPAL_CLIENT_ID)}&currency=USD`;
    script.onload = () => resolve(window.paypal);
    script.onerror = reject;
    document.head.appendChild(script);
  });
}

// Renderizar botón de PayPal
async function renderPayPalButton(amount) {
  const container = document.getElementById("paypal-button-container");
  container.innerHTML = "";
  if (!amount || amount <= 0) return;

  try {
    const paypal = await loadPayPalSDK();
    paypal.Buttons({
      style: { color: "blue", shape: "rect", label: "pay" },
      createOrder: (data, actions) => actions.order.create({
        purchase_units: [{ amount: { value: amount.toFixed(2) } }]
      }),
      onApprove: (data, actions) => actions.order.capture().then(details => {
        alert(`✅ Pago completado por ${details.payer.name.given_name}`);
      }),
      onError: err => {
        console.error("PayPal error:", err);
        alert("❌ Error al procesar el pago con PayPal");
      }
    }).render(container);
  } catch (err) {
    console.error("Error cargando SDK:", err);
    container.innerHTML = "<small style='color:red'>Error al cargar PayPal. Intenta recargar.</small>";
  }
}

// Configuración general
document.addEventListener("DOMContentLoaded", () => {
  const cards = document.querySelectorAll(".card");
  const priceInput = document.getElementById("price");
  const paymentMethods = document.getElementById("payment-methods");
  const paypalLink = document.getElementById("paypalme");

  paypalLink.href = `https://www.paypal.me/${PAYPALME_USER}`;
  paypalLink.textContent = `paypal.me/${PAYPALME_USER}`;

  cards.forEach(card => {
    card.addEventListener("click", () => {
      cards.forEach(c => c.classList.remove("active"));
      card.classList.add("active");
      selectedPrice = parseFloat(card.dataset.price);
      priceInput.value = `$${selectedPrice.toFixed(2)}`;
      paymentMethods.style.display = "block";
      renderPayPalButton(selectedPrice);
    });
  });

  document.getElementById("order-form").addEventListener("submit", e => {
    e.preventDefault();
    const uid = document.getElementById("uid").value.trim();
    const platform = document.getElementById("platform").value;
    const country = document.getElementById("country").value;
    const price = priceInput.value;

    if (!/^\d{5,20}$/.test(uid)) {
      alert("Ingresa un ID válido (solo números).");
      return;
    }

    const mailto = `mailto:aroontigre@gmail.com?subject=Pedido UC PUBG (${uid})&body=ID del jugador: ${uid}%0APlataforma: ${platform}%0APaís: ${country}%0APrecio: ${price}`;
    window.location.href = mailto;
  });
});
</script>
</body>
</html>
