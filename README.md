<html>

<head>

    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.5.1/dist/leaflet.css"
        integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ=="
        crossorigin="" />
    <script src="https://unpkg.com/leaflet@1.5.1/dist/leaflet.js"
        integrity="sha512-GffPMF3RvMeYyc1LWMHtK8EbPv0iNZ8/oTtHPx9/cc2ILxQ+u905qIwdpULaqDkyBKgOaB57QTMg7ztg8Jm2Og=="
        crossorigin="">
        </script>
</head>

<body>

    <div id="mapid" style="width: 90vw; height: 90vh;"></div>
    <script>

        navigator.geolocation.getCurrentPosition(
            function (position) {

                var mymap = L.map('mapid', {
                    center: [position.coords.latitude, position.coords.longitude],
                    zoom: 13
                });
                L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw', {
                    maxZoom: 18,
                    id: 'mapbox.streets'
                }).addTo(mymap);
                L.marker([position.coords.latitude, position.coords.longitude]).addTo(mymap).bindPopup("<b>Hello world!</b><br />Мы здесь").openPopup();
            }
        );

        polylines = polylines.map(function (item) {
            let latitude1 = item.coordinates[0][0][0];
            let longitude1 = item.coordinates[0][0][1];
            let latitude2 = item.coordinates[0][1][0];
            let longitude2 = item.coordinates[0][1][1];
            let distance = Math.sqrt(Math.pow((latitude1 - latitude2), 2) + Math.pow((longitude1 - longitude2), 2));
            return { type: item.type, distance: distance };
        });
        console.log(polylines);
    </script>
</body>

</html>
