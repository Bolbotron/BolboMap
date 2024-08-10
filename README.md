# BolboMap
Maps that includes cheapest petrol
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gas Price Map</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
    <style>
        #map {
            height: 600px;
        }
    </style>
</head>
<body>
    <h1>Gas Price Map</h1>
    <div id="map"></div>

    <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    <script>
        // Initialize the map
        var map = L.map('map').setView([51.505, -0.09], 13);

        // Set up the OpenStreetMap layer
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        // Example marker
        var marker = L.marker([51.5, -0.09]).addTo(map);
        marker.bindPopup("<b>Gas Price</b><br>$2.50").openPopup();

        // Add click event to add markers
        function onMapClick(e) {
            var price = prompt("Enter gas price:");
            if (price) {
                var newMarker = L.marker(e.latlng).addTo(map);
                newMarker.bindPopup("<b>Gas Price</b><br>$" + price).openPopup();
                // Here you'd send the data to your backend server to store it
            }
        }

        map.on('click', onMapClick);
    </script>
</body>
</html>
