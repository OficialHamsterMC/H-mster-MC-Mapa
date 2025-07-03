<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>HamsterMC - Mapa Minecraft</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background: #222;
      color: white;
      padding: 10px 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    header h1 {
      font-size: 1.2rem;
    }

    #back-btn {
      background: #fff;
      color: #222;
      padding: 6px 12px;
      text-decoration: none;
      border-radius: 6px;
      font-weight: bold;
      font-size: 0.9rem;
    }

    #map {
      flex-grow: 1;
      width: 100%;
    }
  </style>
</head>
<body>

  <header>
    <h1>🗺️ Mapa de HamsterMC</h1>
    <a href="HámsterMC.html" id="back-btn">⬅️ Volver</a>
  </header>

  <div id="map"></div>

  <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
  <script>
    var map = L.map('map', {
      crs: L.CRS.Simple,
      minZoom: -2,
      maxZoom: 4,
    });

    var w = 2048; // Ancho en píxeles
    var h = 2048; // Alto en píxeles
    var imageUrl = 'map_minecraft.png';
    var bounds = [[0,0], [h,w]];

    L.imageOverlay(imageUrl, bounds).addTo(map);
    map.fitBounds(bounds);

    L.marker([h/2, w/2]).addTo(map)
      .bindPopup('Centro del mundo')
      .openPopup();
  </script>

</body>
</html>
