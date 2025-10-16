# Ismewel-Top-Up
Página web para recargar UC de PUBG Mobile con PayPal y Banco Pichincha.
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Recargas oficiales — UC PUBG Mobile</title>
  <style>
    :root {
      --primary:#ff6600;
      --accent:#ff9900;
      --bg:#ffffff;
      --card-bg:#f5f5f5;
      --text:#111111;
      --muted:#555555;
      --btn:#003087;
    }
    *{box-sizing:border-box;}
    body{margin:0;font-family:'Poppins',sans-serif;background:var(--bg);color:var(--text);}
    header{padding:25px 10px;text-align:center;border-bottom:2px solid var(--accent);}
    header h1{font-size:28px;margin:0;color:var(--primary);}
    header p{margin:5px 0 0;color:var(--muted);}
    main{max-width:1100px;margin:30px auto;padding:0 20px;display:grid;grid-template-columns:3fr 1.2fr;gap:25px;}
    @media(max-width:900px){main{grid-template-columns:1fr;}}
    .catalog{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px;}
    .card{background:var(--card-bg);border-radius:12px;padding:20px;text-align:center;box-shadow:0 0 10px rgba(0,0,0,0.1);cursor:pointer;transition:transform .2s;}
    .card:hover{transform:translateY(-5px);}
    .card h3{margin:0;font-size:22px;font-weight:700;}
    .price{margin-top:10px;font-size:18px;font-weight:600;color:var(--primary);}
    .btn{margin-top:12px;background:var(--btn);color:#fff;padding:10px 14px;border:none;border-radius:8px;cursor:pointer;font-weight:600;transition:background .2s;width:100%;}
    .btn:hover{background:#002060;}
    .sidebar{background:var(--card-bg);border-radius:12px;padding:20px;box-shadow:0 0 10px rgba(0,0,0,0.1);}
    label{display:block;margin-top:10px;font-size:14px;color:var(--muted);}
    input,select{width:100%;margin-top:5px;padding:10px;border-radius:6px;border:1px solid #ddd;background:#fff;color:#111;}
    .order-summary{margin-top:15px;padding:10px;border:1px dashed var(--accent);border-radius:8px;font-size:13px;color:var(--muted);}
    footer{text-align:center;padding:20px;margin-top:40px;border-top:1px solid var(--accent);font-size:13px;color:var(--muted);}
    .verified{color:#009900;font-weight:700;font-size:14px;margin-bottom:10px;}
    .logos img{height:30px;margin-right:8px;}
  </style>
</head>
<body>
  <header>
    <h1>Recargas oficiales</h1>
    <p class="verified">✅ Sitio verificado y seguro</p>
    <p>Recarga UC de PUBG Mobile con PayPal o Banco Pichincha</p>
  </header>

  <main>
    <section class="catalog">
      <div class="card" data-uc="60" data-price="1"><h3>60 UC</h3><p class="price">$1.00</p></div>
      <div class="card" data-uc="300" data-price="2"><h3>300 UC</h3><p class="price">$2.00</p></div>
      <div class="card" data-uc="680" data-price="13.99"><h3>680 UC</h3><p class="price">$13.99</p></div>
      <div class="card" data-uc="1320" data-price="23.99"><h3>1320 UC</h3><p class="price">$23.99</p></div>
      <div class="card" data-uc="2640" data-price="53.99"><h3>2640 UC</h3><p class="price">$53.99</p></div>
      <div class="card" data-uc="8100" data-price="103.99"><h3>8100 UC</h3><p class="price">$103.99</p></div>
    </section>

    <aside class="sidebar">
      <form id="order-form">
        <label>Nick de PUBG</label>
        <input type="text" id="nick" required placeholder="Tu nombre en el juego">

        <label>Plataforma</label>
        <select id="platform" required>
          <option value="">Selecciona una</option>
          <option value="Android">Android</option>
          <option value="iOS">iOS</option>
        </select>

        <label>Paquete seleccionado</label>
        <input type="text" id="pack" readonly required placeholder="Selecciona un paquete">

        <label>Precio final (USD)</label>
        <input type="text" id="price" readonly required placeholder="$0.00">

        <label>País</label>
        <input type="text" id="country" required placeholder="Ej: Ecuador">

        <label>Método de pago</label>
        <select id="method" required>
          <option value="">Selecciona método</option>
          <option value="paypal">PayPal / Tarjeta de crédito</option>
          <option value="bank">Banco Pichincha (solo Ecuador)</option>
        </select>

        <div class="order-summary">
          <p>💳 Banco Pichincha (solo Ecuador): <strong>2212896512</strong></p>
          <p>🌐 PayPal / Tarjeta: 
            <a href="https://www.paypal.me/Ismewel" target="_blank" style="color:var(--accent)">
              paypal.me/Ismewel
            </a>
          </p>
          <div class="logos">
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/04/Visa.svg" alt="Visa">
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/0e/Mastercard-logo.svg" alt="MasterCard">
            <img src="https://upload.wikimedia.org/wikipedia/commons/b/b5/PayPal.svg" alt="PayPal">
          </div>
          <small>Tras pagar, envía el comprobante a <strong>quinteroismael38@gmail.com</strong> con tu nick y país.</small>
        </div>

        <button class="btn" type="submit">Enviar pedido</button>
      </form>
    </aside>
  </main>

  <footer>© 2025 Recargas oficiales — Todos los derechos reservados</footer>

  <script>
    // Seleccionar paquete y poner precio exacto
    document.querySelectorAll(".card").forEach(card=>{
      card.addEventListener("click",()=>{
        const uc = card.dataset.uc;
        const price = card.dataset.price;
        document.getElementById("pack").value = `${uc} UC`;
        document.getElementById("price").value = `$${price}`;
        window.scrollTo({top:document.getElementById("order-form").offsetTop-80,behavior:"smooth"});
      });
    });

    // Enviar orden por mail
    document.getElementById("order-form").addEventListener("submit",e=>{
      e.preventDefault();
      const nick = document.getElementById("nick").value;
      const platform = document.getElementById("platform").value;
      const pack = document.getElementById("pack").value;
      const price = document.getElementById("price").value;
      const country = document.getElementById("country").value;
      const method = document.getElementById("method").value;
      const subject = encodeURIComponent(`Nueva orden UC - ${pack} - ${nick}`);
      const body = encodeURIComponent(
        `Orden de recarga:\n\nNick: ${nick}\nPlataforma: ${platform}\nPaquete: ${pack}\nPrecio: ${price}\nPaís: ${country}\nMétodo: ${method}\n\nEnviar comprobante a quinteroismael38@gmail.com`
      );
      window.location.href = `mailto:quinteroismael38@gmail.com?subject=${subject}&body=${body}`;
    });
  </script>
</body>
</html>
