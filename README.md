# VitalFi (Flutter)

App experimental offline para Android que intenta detectar signos de vida bajo escombros mediante análisis de variaciones de señal Wi‑Fi (RSSI), con visualización tipo radar 2D/3D.

> **Aviso:** VitalFi es un prototipo experimental de investigación / demostración. **No sustituye** equipos profesionales de búsqueda y rescate ni protocolos oficiales. Úsala solo como apoyo experimental y con criterio.

## Qué hace

VitalFi combina un smartphone Android y un router Wi‑Fi convencional para observar fluctuaciones del canal inalámbrico. A partir de esas lecturas, la app estima (de forma experimental):

- Presencia de posibles blancos en el área de cobertura
- Confianza vital (indicador heurístico de actividad)
- Frecuencia respiratoria estimada (RPM)
- Posición aproximada (coordenadas / proximidad)
- Profundidad estimada bajo escombros

La interfaz presenta un radar 2D/3D para inspeccionar detecciones y abrir el detalle de cada punto.

## Características

- Funciona **offline** (sin servidor ni cuenta)
- Lectura de RSSI / entorno Wi‑Fi desde el dispositivo
- Calibración inicial (~30 s) antes de escanear
- Radar interactivo 2D/3D
- Detalle por detección (vitalidad, respiración, proximidad, profundidad)
- Orientado a escenarios de colapso / desastre (uso experimental)

## Requisitos de hardware

| Elemento | Notas |
|----------|--------|
| Smartphone Android | Permisos de ubicación / Wi‑Fi según versión de Android |
| Router Wi‑Fi | Preferible **2.4 GHz**; dual-band puede servir, pero 2.4 GHz suele dar lecturas más estables para este tipo de ensayo |
| Distancia | El emisor (router) debe estar relativamente cerca de la zona a inspeccionar |

## Requisitos de desarrollo

- [Flutter](https://docs.flutter.dev/get-started/install) (canal estable recomendado)
- Android SDK / dispositivo o emulador Android
- Dart SDK (incluido con Flutter)

Comprueba tu entorno:

```bash
flutter doctor
```

## Instalación

```bash
git clone https://github.com/carlosmundaray/vitalfi_flutter.git
cd vitalfi_flutter
flutter pub get
```

## Ejecutar

Con un dispositivo Android conectado (o emulador):

```bash
flutter run
```

Build de release:

```bash
flutter build apk
# o
flutter build appbundle
```

## Uso rápido (concepto)

1. Coloca el router Wi‑Fi cerca de la zona a inspeccionar (idealmente 2.4 GHz).
2. Conecta el teléfono a esa red (o configura el flujo que indique la app).
3. Abre VitalFi y completa la **calibración** (~30 s).
4. Observa el **radar** 2D/3D.
5. Toca un punto detectado para ver confianza vital, RPM, proximidad y profundidad estimada.

Los pasos exactos de UI pueden cambiar a medida que avance el puerto Flutter.

## Estructura del proyecto

```
vitalfi_flutter/
├── android/          # Proyecto nativo Android
├── lib/              # Código Dart (UI, sensores, radar, lógica RSSI)
├── test/             # Pruebas
├── pubspec.yaml      # Dependencias
├── LICENSE           # GPL-3.0
└── README.md
```

> Si aún no hay código de app en el repo, esta estructura es la objetivo al generar el proyecto Flutter (`flutter create`).

## Limitaciones conocidas

- Resultados **heurísticos**: ruido, multipath, movimiento cercano y el propio entorno alteran el RSSI.
- Alcance y precisión dependen del router, obstáculos y calibración.
- No está validado como instrumento médico ni de rescate certificado.
- En Android, el acceso a Wi‑Fi/escaneo suele requerir permisos y restricciones del sistema.

## Licencia

Distribuido bajo **GNU General Public License v3.0** — ver [LICENSE](LICENSE).

## Autor

Carlos Mundaray — [@carlosmundaray](https://github.com/carlosmundaray)

## Contribuciones

Issues y pull requests son bienvenidos. Antes de cambios grandes, abre un issue para alinear el enfoque (UI, pipeline RSSI, visualización del radar, etc.).
