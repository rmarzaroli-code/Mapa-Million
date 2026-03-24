<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mapa con botón</title>
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  />
  <style>
    /* Tamaño del mapa */
    #map {
      width: 100%;
      height: 500px;
    }
    /* Estilo del botón */
    #btn {
      position: absolute;
      bottom: 20px;
      left: 20px;
      background-color: green;
      color: white;
      border: none;
      padding: 10px 20px;
      cursor: pointer;
      font-size: 16px;
      border-radius: 5px;
      z-index: 1000;
    }
  </style>
</head>
<body>

<div id="map"></div>
<button id="btn">1m</button>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script>
  // Crear el mapa
  const map = L.map('map').setView([0, 0], 2);

  // Agregar mapa base
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap contributors'
  }).addTo(map);

  let marker = null; // Para guardar el marcador

  // Cuando se hace clic en el botón
  document.getElementById('btn').addEventListener('click', () => {
    if (marker) {
      // Si ya hay un marcador, se elimina
      map.removeLayer(marker);
      marker = null;
    } else {
      // Crear un marcador en posición aleatoria
      const lat = (Math.random() * 180) - 90;   // latitud entre -90 y 90
      const lng = (Math.random() * 360) - 180;  // longitud entre -180 y 180
      marker = L.marker([lat, lng], {icon: L.icon({
        iconUrl: 'https://maps.google.com/mapfiles/ms/icons/red-dot.png',
        iconSize: [32, 32],
        iconAnchor: [16, 32],
      })}).addTo(map);
    }
  });
</script>

</body>
</html>
