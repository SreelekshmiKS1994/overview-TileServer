
# TileServer

TileServer is a powerful tool for serving map tiles efficiently. This server can handle raster and vector tiles and supports multiple protocols for easy integration with various mapping applications.

## Features
- Serves raster and vector map tiles
- Supports XYZ, TMS, and WMTS protocols
- Efficient tile caching for faster performance
- Scalable to handle multiple requests simultaneously
- Compatible with popular GIS software and libraries

## Requirements
- Node.js (for Tileserver GL)
- Python (for TileStache)
- Mapnik (for custom rendering)
- Docker (optional, for containerized deployment)

## Installation

### Using Node.js (Tileserver GL)
1. **Install Node.js**: Make sure you have Node.js installed on your system.
2. **Install Tileserver GL**:
   ```bash
   npm install -g tileserver-gl
   ```
3. **Run Tileserver GL**:
   ```bash
   tileserver-gl ./path-to-config.json
   ```

### Using Docker
1. **Install Docker**: Ensure Docker is installed and running on your system.
2. **Pull the Tileserver GL Docker image**:
   ```bash
   docker pull maptiler/tileserver-gl
   ```
3. **Run the Docker container**:
   ```bash
   docker run --rm -it -v $(pwd):/data -p 8080:80 maptiler/tileserver-gl
   ```

## Configuration
Tileserver can be configured using a JSON configuration file. Below is an example configuration (`config.json`):

```json
{
  "options": {
    "paths": {
      "root": "/data"
    }
  },
  "styles": {
    "style": {
      "style": "style.json",
      "tilejson": {
        "type": "overlay"
      }
    }
  }
}
```

## Usage

### Accessing Tiles
Once the TileServer is running, you can access the tiles through the following URL patterns:
- **Raster Tiles**: `http://localhost:8080/data/{z}/{x}/{y}.png`
- **Vector Tiles**: `http://localhost:8080/data/{z}/{x}/{y}.pbf`

### Integrating with Leaflet
To use the tiles in a Leaflet map, add the following code to your Leaflet setup:

```javascript
L.tileLayer('http://localhost:8080/data/{z}/{x}/{y}.png', {
  maxZoom: 18,
  attribution: 'Map data © OpenStreetMap contributors'
}).addTo(map);
```

## Contributing
Contributions are welcome! Please open an issue or submit a pull request on GitHub.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
