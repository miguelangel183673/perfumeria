<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Perfumería juancho S.A.S</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 20px;
      color: #333;
    }
    header {
      text-align: center;
      background-color: #6a1b9a;
      color: white;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 30px;
    }
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
    }
    .product {
      background: white;
      border-radius: 10px;
      padding: 15px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      text-align: center;
    }
    .product img {
      max-width: 100%;
      border-radius: 10px;
    }
    .product h3 {
      margin: 10px 0;
    }
    .cart, .invoice {
      margin-top: 30px;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }
    .btn {
      background-color: #6a1b9a;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 10px;
    }
    .btn:hover {
      background-color: #4a0072;
    }
  </style>
</head>
<body>

<header>
  <h1>Bienvenido a nuestra perfumería juancho S.A.S</h1>
  <p>Gracias por preferirnos</p>
</header>

<div class="container" id="product-list"></div>

<div class="cart">
  <h2>Carrito de Compras</h2>
  <ul id="cart-items"></ul>
  <p>Total: $<span id="total">0.00</span></p>
  <button class="btn" onclick="finalizarCompra()">Finalizar Compra</button>
</div>

<div class="invoice" id="invoice" style="display: none;"></div>

<script>
  const productos = [
    { id: 1, nombre: "Perfume Elegancia", precio: 15.000, imagen: "https://via.placeholder.com/300x200?text=Elegancia" },
    { id: 2, nombre: "Loción Fresh", precio: 15.000, imagen: "https://via.placeholder.com/300x200?text=Fresh" },
    { id: 3, nombre: "Fragancia Nocturna", precio: 15.000, imagen: "https://via.placeholder.com/300x200?text=Nocturna" }
  ];

  const carrito = [];

  function mostrarProductos() {
    const lista = document.getElementById('product-list');
    productos.forEach(prod => {
      const div = document.createElement('div');
      div.className = 'product';
      div.innerHTML = `
        <img src="${prod.imagen}" alt="${prod.nombre}"/>
        <h3>${prod.nombre}</h3>
        <p>Precio: $${prod.precio.toFixed(2)}</p>
        <input type="number" id="cant-${prod.id}" min="1" value="1" style="width: 60px;">
        <br>
        <button class="btn" onclick="agregarAlCarrito(${prod.id})">Agregar al Carrito</button>
      `;
      lista.appendChild(div);
    });
  }

  function agregarAlCarrito(id) {
    const cantidad = parseInt(document.getElementById(`cant-${id}`).value);
    const producto = productos.find(p => p.id === id);
    const existente = carrito.find(item => item.id === id);
    if (existente) {
      existente.cantidad += cantidad;
    } else {
      carrito.push({ ...producto, cantidad });
    }
    actualizarCarrito();
  }

  function actualizarCarrito() {
    const lista = document.getElementById('cart-items');
    const totalSpan = document.getElementById('total');
    lista.innerHTML = '';
    let total = 0;
    carrito.forEach(item => {
      const li = document.createElement('li');
      li.textContent = `${item.nombre} x${item.cantidad} - $${(item.precio * item.cantidad).toFixed(2)}`;
      lista.appendChild(li);
      total += item.precio * item.cantidad;
    });
    totalSpan.textContent = total.toFixed(2);
  }

  function finalizarCompra() {
    if (carrito.length === 0) {
      alert("El carrito está vacío.");
      return;
    }
    const invoice = document.getElementById('invoice');
    invoice.innerHTML = '<h2>Factura</h2>';
    let total = 0;
    carrito.forEach(item => {
      const p = document.createElement('p');
      p.textContent = `${item.nombre} x${item.cantidad} - $${(item.precio * item.cantidad).toFixed(2)}`;
      invoice.appendChild(p);
      total += item.precio * item.cantidad;
    });
    const totalP = document.createElement('p');
    totalP.innerHTML = `<strong>Total a pagar: $${total.toFixed(2)}</strong>`;
    invoice.appendChild(totalP);
    invoice.style.display = 'block';
    alert("¡Compra exitosa! Gracias por su preferencia.");
    carrito.length = 0;
    actualizarCarrito();
  }

  mostrarProductos();
</script>

</body>
</html>
