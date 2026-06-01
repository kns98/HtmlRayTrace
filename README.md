# Lighting Showcase — JavaScript Raytracer

Lighting Showcase is a single-file JavaScript raytracing demo that renders an interactive 3D room scene directly in the browser using a 2D canvas. It includes dynamic lighting, a built-in furnished room, a demo camera path, manual navigation controls, recursive BVH acceleration, and Wavefront OBJ model loading.

## Features

* CPU-based ray tracing rendered into an HTML5 canvas
* Built-in room scene with walls, floor, ceiling, sofa, rug, table, cabinet, plant, lamp, and screen
* Direct lighting from a ceiling panel and lamp
* Emissive materials for visible light sources
* Animated lighting sequence with brightness transitions
* Recursive BVH bounding boxes for triangle acceleration
* Demo camera path for automatic scene walkthrough
* Manual camera movement using keyboard and mouse
* Render scale options for balancing quality and performance
* Wavefront `.obj` import
* Optional `.mtl` material support when loaded together with the OBJ file
* Drag-and-drop file loading in the browser

## Getting Started

### 1. Create an HTML file

Create a blank HTML file, for example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Lighting Showcase</title>
</head>
<body>
  <script src="lighting-showcase-onefile.js"></script>
</body>
</html>
```

### 2. Add the JavaScript file

Place the JavaScript file in the same folder as the HTML file.

Example folder structure:

```text
project-folder/
├── index.html
└── lighting-showcase-onefile.js
```

### 3. Open in a browser

Open `index.html` in a modern browser.

The application will automatically start and render the built-in room scene.

## Controls

| Control    | Action                                |
| ---------- | ------------------------------------- |
| `W`        | Move forward                          |
| `A`        | Move left                             |
| `S`        | Move backward                         |
| `D`        | Move right                            |
| `Q`        | Move down                             |
| `E`        | Move up                               |
| Mouse drag | Look around                           |
| `F`        | Play or pause lighting/demo animation |
| `T`        | Restart demo                          |
| `M`        | Switch to manual camera               |
| `P`        | Switch to demo camera                 |
| `R`        | Reset camera                          |
| `+` / `=`  | Increase render scale                 |
| `-` / `_`  | Decrease render scale                 |

## User Interface

The on-screen control panel includes:

* Play/Pause button
* Restart button
* Manual camera button
* Demo camera button
* Reset camera button
* Render scale selector
* OBJ/MTL file loader
* Current scene status
* Triangle count
* Lighting state
* Camera mode

## Loading OBJ Models

The application supports loading Wavefront `.obj` files.

To load a model:

1. Click the file input in the control panel, or drag files into the browser window.
2. Select an `.obj` file.
3. Optionally select related `.mtl` files at the same time.
4. The model will be imported into the existing room scene.

When loaded, the OBJ model is automatically scaled and positioned inside the built-in room.

## Supported File Types

| File Type | Purpose                       |
| --------- | ----------------------------- |
| `.obj`    | 3D model geometry             |
| `.mtl`    | Optional material definitions |

## Rendering System

The renderer casts rays from the camera into the scene and shades the first visible triangle hit by each ray. Lighting is computed using direct illumination from scene lights, material color, emissive surfaces, distance attenuation, and shadow checks.

The scene geometry is stored as triangles. A recursive BVH structure is used to accelerate ray-triangle intersection tests, making larger scenes more practical than a simple brute-force triangle loop.

## Scene Structure

The built-in scene contains:

* Enclosed room
* Floor and ceiling
* Colored side walls
* Back wall
* Ceiling light panel
* Sofa
* Cushions
* Rug
* Coffee table
* Cabinet
* Plant and pot
* Floor lamp
* Wall-mounted screen

## Performance Notes

This project uses CPU ray tracing, so performance depends heavily on:

* Browser speed
* Screen resolution
* Render scale
* Number of triangles in the scene
* Complexity of imported OBJ models

For better performance, use a lower render scale such as 25% or 50%.

For better image quality, use 75% or 100%, but expect slower rendering.

## Browser Requirements

A modern browser with support for:

* JavaScript ES6 classes
* HTML5 canvas
* File API
* Drag-and-drop events
* `requestAnimationFrame`

Recommended browsers:

* Chrome
* Edge
* Firefox
* Safari

## Project Type

This is a self-contained browser-based raytracing demo. It does not require:

* npm
* bundlers
* external libraries
* WebGL
* server-side code

Everything runs locally in the browser.

## Limitations

* Rendering is CPU-based and may be slow at high resolutions.
* The raytracer currently uses direct lighting rather than full global illumination.
* OBJ material support is basic.
* Texture maps are not supported.
* Very large OBJ files may reduce performance significantly.
* The built-in scene remains active when an OBJ model is loaded.

## Suggested Improvements

Possible future enhancements include:

* Web Worker rendering
* Progressive rendering
* Anti-aliasing
* Reflections and recursive ray bounces
* Texture support
* Area light sampling
* Physically based materials
* Scene export/import
* Separate scene configuration files
* WebGL or WebGPU acceleration

## License

Add your preferred license here.

Example:

```text
MIT License
```

## Credits

Lighting Showcase is a single-file JavaScript port of a C# WinForms raytracer project. It preserves the original raytracing behavior while adapting the application to run directly in a browser.
