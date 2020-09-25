# AR.js - Augmented Reality on the Web

Ar.js ist eine lightweight Library für die Entwicklung von Web AR-Anwendungen.
Es können Marker und Bilder, sowie Location basierte Anwendungen erstellt werden.
[Dokumentation](https://ar-js-org.github.io/AR.js-Docs/)

## NFT Marker Creator
[Web App](https://carnaux.github.io/NFT-Marker-Creator/) oder die [Node App](https://github.com/Carnaux/NFT-Marker-Creator) zur Erstellung der Marker mit [Anleitung](https://github.com/Carnaux/NFT-Marker-Creator/wiki/Creating-good-markers) für gut geeignete Marker.

## [A-Frame](https://aframe.io/)
Webframework zur Erstellung von 3D/AR und VR Anwendungen
[Tutorial](https://aframe.io/docs/1.0.0/guides/building-a-basic-scene.html)


## Marker Beispiel:

Die Beispiel-Anwendung kann den [Hiro](https://github.com/artoolkit/ARToolKit5/blob/master/doc/patterns/Hiro%20pattern.pdf) und den [Kanji](https://github.com/artoolkit/ARToolKit5/blob/master/doc/patterns/Kanji%20pattern.pdf) Marker erkennen und legt entsprechende Objekte über die Marker.

![Hiro](https://raw.githubusercontent.com/saspengler/markerReco/master/marker/hiro.png) ![Kanji](https://raw.githubusercontent.com/saspengler/markerReco/master/marker/kanji.png){:width="50%"}


*** 

Nötige Erweiterung für eigene Marker/Images:

* Erstellen eines neuen Projektes mit folgendem Code:

```
<script src="https://cdn.jsdelivr.net/gh/aframevr/aframe@1c2407b26c61958baa93967b5412487cd94b290b/dist/aframe-master.min.js"></script>
<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar-nft.js"></script>

<style>
  .arjs-loader {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 9999;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .arjs-loader div {
    text-align: center;
    font-size: 1.25em;
    color: white;
  }
</style>

<body style="margin : 0px; overflow: hidden;">
  <!-- minimal loader shown until image descriptors are loaded -->
  <div class="arjs-loader">
    <div>Loading, please wait...</div>
  </div>
  <a-scene
    vr-mode-ui="enabled: false;"
    renderer="logarithmicDepthBuffer: true;"
    embedded
    arjs="trackingMethod: best; sourceType: webcam;debugUIEnabled: false;"
  >
    <!-- we use cors proxy to avoid cross-origin problems -->
    <a-nft
      type="nft"
      url="https://arjs-cors-proxy.herokuapp.com/https://raw.githack.com/AR-js-org/AR.js/master/aframe/examples/image-tracking/nft/trex/trex-image/trex"
      smooth="true"
      smoothCount="10"
      smoothTolerance=".01"
      smoothThreshold="5"
    >
      <a-entity
        gltf-model="https://arjs-cors-proxy.herokuapp.com/https://raw.githack.com/AR-js-org/AR.js/master/aframe/examples/image-tracking/nft/trex/scene.gltf"
        scale="5 5 5"
        position="50 150 0"
      >
      </a-entity>
    </a-nft>
    <a-entity camera></a-entity>
  </a-scene>
</body>
```

* Marker im NFT Marker Creator erstellen und ins Projekt einbinden
* Ausführen auf einem Server
* Öffnen der Webseite auf einem mobilen Endgerät
* Scannen des verwendeten Bildes
