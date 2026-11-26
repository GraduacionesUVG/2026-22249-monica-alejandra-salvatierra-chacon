# AR Tour Kaminaljuyú (iOS)

## Descripción

El Parque Arqueológico Kaminaljuyú ya contaba con una aplicación para recorrer el sitio con realidad aumentada, pero solo estaba disponible para Android. Eso dejaba fuera a una parte importante de los visitantes, los que usan iPhone, que no tenían forma de acceder a esta herramienta para conocer el patrimonio arqueológico del parque de manera interactiva.

Este proyecto resuelve ese problema con una aplicación nativa para iOS. No es solo una migración directa, puesto que la arquitectura se rediseñó desde cero en Swift y se incorporaron funcionalidades que la versión original no contemplaba, como la posibilidad de ofrecer el recorrido completo en español o en inglés.

La aplicación guía al visitante por los distintos puntos de interés del parque usando su ubicación. Cuando el usuario se acerca a un montículo, la cámara despliega un modelo tridimensional de la estructura sobre la imagen real, y una guía virtual en video acompaña el recorrido con narración y subtítulos. El usuario también puede consultar un mapa con la ruta completa y elegir el idioma de toda la experiencia desde el menú principal.

La aplicación depende de la ubicación física del usuario y solo funciona correctamente dentro del Parque Arqueológico Kaminaljuyú. Por eso, el video en [demo/demo.mp4](demo/demo.mp4) es la evidencia del funcionamiento completo del recorrido en el sitio real.

**Mi aporte**

Mi trabajo se concentró en el diseño de la arquitectura modular general de la aplicación y en la integración entre los distintos módulos, incluyendo el bus de eventos, la inyección de dependencias y el manejo centralizado del estado del recorrido. Además, desarrollé el módulo de lenguaje, encargado de la experiencia en español e inglés. 

## Estructura del Repositorio

```
.
├── capturas/                   # capturas de pantalla de la app (ver sección Capturas)
├── demo/
│   └── demo.mp4                # Video demostrativo del recorrido completo en el parque
├── docs/
│   ├── informe_final.pdf       # Informe final del proyecto
│   └── consentimiento_firmado.pdf
├── src/
│   ├── ArTourKaminaljuyu/      # Código fuente de la app iOS (Xcode project)
│   ├── PerformanceTests/       # Pruebas de rendimiento
│   ├── .env.example            # Referencia de variables necesarias (ver Secrets.xcconfig.example)
│   └── README.md               # README original del proyecto iOS
└── README.md
```

## Tecnologías Utilizadas

- Swift como lenguaje de programación.
- SwiftUI para la interfaz, con UIKit en la vista de realidad aumentada.
- Combine para el manejo de estado y la comunicación entre módulos.
- CoreLocation para la ubicación del usuario.
- Google Maps SDK for iOS (`GoogleMaps`, versión `~> 9.0`) y `GooglePlaces` (`~> 9.0`), instalados con CocoaPods.
- ARKit y SceneKit para la realidad aumentada.
- AVFoundation y AVKit para la reproducción de los videos de la guía virtual.
- Swift Testing para las pruebas funcionales y de arquitectura.
- XCTest para las pruebas de rendimiento.
- CocoaPods como gestor de dependencias.

## Requisitos Previos

- Mac con Xcode 26 o superior.
- CocoaPods instalado (`sudo gem install cocoapods` o `brew install cocoapods`).
- iPhone físico con iOS 26.0 o superior. La realidad aumentada no funciona en el simulador, así que para probar el recorrido completo se necesita un dispositivo real.
- Una API key de Google Maps con el SDK de Maps para iOS habilitado.
- La aplicación solo funciona completamente dentro del Parque Arqueológico Kaminaljuyú, ya que depende de la ubicación real del usuario dentro del sitio.

## Instalación

1. Clonar el repositorio y entrar a la carpeta del proyecto:

   ```bash
   git clone https://github.com/GraduacionesUVG/2026-22249-monica-alejandra-salvatierra-chacon.git
   cd 2026-22249-monica-alejandra-salvatierra-chacon/src/ArTourKaminaljuyu
   ```

2. Instalar las dependencias con CocoaPods (esto también genera el archivo `.xcworkspace`):

   ```bash
   pod install
   ```

3. Configurar la API key de Google Maps copiando el archivo de ejemplo:

   ```bash
   cp Secrets.xcconfig.example Secrets.xcconfig
   ```

   Después, dentro de `Secrets.xcconfig`, reemplazar el valor de la variable:

   ```
   GOOGLE_MAPS_API_KEY = tu_api_key_aqui
   ```

   En este proyecto la configuración real va en `Secrets.xcconfig`. El archivo [src/.env.example](src/.env.example) se incluye y muestra el nombre de la variable necesaria.

4. Abrir el proyecto en Xcode usando el workspace, no el `.xcodeproj`, porque las dependencias de CocoaPods solo se cargan desde ahí:

   ```bash
   open ArTourKaminaljuyu.xcworkspace
   ```

5. Compilar y ejecutar la aplicación. En Xcode, seleccionar el esquema `ArTourKaminaljuyu`, elegir como destino un iPhone físico conectado y ejecutar con ⌘R. La primera vez, aceptar los permisos de cámara y ubicación que solicita la aplicación.

## Capturas

Las capturas de pantalla se encuentran en la carpeta [/capturas](capturas) (13 imágenes).

- [captura-01](capturas/captura-01.jpg) y [captura-02](capturas/captura-02.jpg): menú principal en español e inglés.
- [captura-03](capturas/captura-03.jpg): términos y condiciones.
- [captura-04](capturas/captura-04.jpg): controles del tour de realidad aumentada.
- [captura-05](capturas/captura-05.jpg) a [captura-08](capturas/captura-08.jpg): pantallas del recorrido con realidad aumentada, mapa y guía virtual.
- [captura-09](capturas/captura-09.jpg): estructura modular del proyecto en Xcode.
- [captura-10](capturas/captura-10.jpg) a [captura-12](capturas/captura-12.jpg): código del bus de eventos y sus pruebas.
- [captura-13](capturas/captura-13.jpg): pruebas automatizadas pasando.

## Demo

El video demostrativo se encuentra en [demo/demo.mp4](demo/demo.mp4).

## Documentación

- El informe final del proyecto está disponible en [informe final](docs/informe_final.pdf).
- El consentimiento de uso de foto y video firmado se encuentra en [consentimiento firmado](docs/consentimiento_firmado.pdf).

## Autores

- Mónica Alejandra Salvatierra Chacón - 22249
- Asesor: Ing. Erick Francisco Marroquín Rodríguez

