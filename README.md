# chufe

## About

chufe is an open source hardware Eurorack power supply by [piruetas](https://piruetas.xyz). It takes 12 V DC from a barrel jack, with reverse polarity protection, and outputs ±12V (from a 20 W isolated DC-DC converter) and +5V (from an L7805 linear regulator) on two 16-pin Eurorack power headers, with an LED for each rail. It is designed to feed a power bus such as [chufebu](https://github.com/piruetasxyz/chufebu). The design is made in KiCad 10 with KiCad's standard libraries plus its own symbol, footprint and 3D model for the DC-DC converter, included in `hardware/bibliotecas/`. Hardware is licensed under CERN-OHL-P-2.0 and documentation under CC-BY-SA-4.0 (see [LICENSE.md](./LICENSE.md)). Documentation, schematic, board render and bill of materials (in Spanish): <https://piruetas.xyz/chufe/>.

## Acerca de

Fuente de alimentación eurorack de [piruetas](https://piruetas.xyz), hecha en KiCad y publicada como hardware de código abierto.

Documentación, esquemático, placa y Bill of materials: <https://piruetas.xyz/chufe/>.

## Características

- Entrada de 12 V DC por jack, con protección contra polaridad inversa.
- Salidas de +12V y -12V desde un convertidor DC-DC aislado de 20 W (URA2412YMD-20WR3).
- Salida de +5V desde un regulador lineal L7805, alimentado desde +12V.
- Dos headers de alimentación Eurorack de 16 pines (2x08), con -12V, GND, +12V y +5V en ambos.
- 4 LEDs indicadores: entrada, -12V, +12V y +5V.
- Placa de 50 × 65 mm, 2 capas, con 4 agujeros de montaje M3.
- Hecha para alimentar un bus como [chufebu](https://github.com/piruetasxyz/chufebu).

## Pines y manual de uso

Los pines de los headers de 16 pines, cómo conectar chufe y las advertencias están en el [manual de uso](https://piruetas.xyz/chufe/#manual-de-uso).

## Revisiones

- `v0.1 rev-a`: fabricada y probada en octubre 2026.
- `v0.1 rev-b`: fabricada y probada en noviembre 2026. Dos headers Eurorack de 16 pines en vez de un header y un conector Molex KK-396, pistas de alimentación más anchas (0.8 mm), C3 cerámico en vez de electrolítico, etiquetas para los LEDs, logo de certificación OSHWA (CL000011) y modelo 3D corregido del convertidor DC-DC.

## Pendiente para rev-1

### Condensadores faltantes

Ahora no hay condensadores en la entrada del convertidor DC-DC ni en sus salidas. rev-a funciona así, pero agregarlos baja el ripple y protege mejor el convertidor:

- Entrada: entre `Net-(D1-K)` (U1 pin 2, después de Q1) y GND. Va después de Q1 para quedar protegido contra polaridad inversa.
- +12V: entre +12V y GND, junto a U1 pin 3.
- -12V: entre -12V y GND, junto a U1 pin 5. Hoy -12V no tiene ningún condensador.

Todos van a GND (que es el mismo nodo que COM y -VIN del convertidor). Cada riel lleva uno de 100 nF lo más cerca posible de los pines de U1, para el ruido de conmutación.

### Sin condensadores electrolíticos

Para que la placa dure más, rev-1 no debería usar condensadores electrolíticos, porque su electrolito líquido se seca con los años. En rev-b C3 ya es cerámico (10 µF / 50 V X5R 1206, LCSC C13585), así que no queda ninguno: los condensadores nuevos también deberían ser cerámicos.

### Materiales sugeridos

- Cerámicos MLCC con dieléctrico X7R: no se secan y son estables con la temperatura. Ojo con la pérdida de capacidad por voltaje DC: un 10 µF / 25 V en 1206 queda en ~4–5 µF a 12 V. Conviene subir el voltaje nominal o el tamaño:
  - Entrada, +12V y -12V: 10 µF / 50 V X7R 1210, más 100 nF en 0805 en cada riel.
  - +5V: C3 ya es 10 µF / 50 V X5R 1206 (C13585) desde rev-b. El L7805 es estable con condensadores cerámicos.
- Los cerámicos no tienen polaridad, así que no hay riesgo de soldar al revés el de -12V.
- Al conectar el jack en caliente, un cerámico solo en la entrada puede generar un pico de voltaje. Dos opciones:
  - Un diodo TVS SMBJ30A (encapsulado SMB) entre `Net-(D1-K)` y GND, que recorta el pico antes del máximo de 36 V del convertidor.
  - Condensadores de polímero sólido en la entrada: no tienen líquido, no se secan y amortiguan mejor que los cerámicos.

## Estructura del repositorio

- [hardware/chufe-v-0-rev-a](./hardware/chufe-v-0-rev-a): proyecto de KiCad (esquemático y placa), los archivos fuente del diseño.
- [hardware/chufe-v-0-rev-a-fab](./hardware/chufe-v-0-rev-a-fab): gerbers y archivos de taladrado para fabricar la placa.
- [hardware/chufe-v-0-rev-a-pcba](./hardware/chufe-v-0-rev-a-pcba): lista de componentes y archivo de posiciones para armado en JLCPCB.
- [hardware/chufe-v-0-rev-b](./hardware/chufe-v-0-rev-b), [hardware/chufe-v-0-rev-b-fab](./hardware/chufe-v-0-rev-b-fab) y [hardware/chufe-v-0-rev-b-pcba](./hardware/chufe-v-0-rev-b-pcba): lo mismo para rev-b.
- [hardware/bibliotecas](./hardware/bibliotecas): símbolo, huella y modelo 3D del convertidor URA2412YMD-20WR3, dibujados por piruetas a partir de la hoja de datos. Van en el repositorio para que el proyecto de KiCad se abra sin instalar bibliotecas adicionales.
- [docs](./docs): documentación, publicada en <https://piruetas.xyz/chufe/>. Las capturas del esquemático y de la placa, y la tabla de Bill of materials, las genera [kicad-retrata](https://github.com/piruetasxyz/kicad-retrata) en cada push (ver [kicad-retrata.yml](./kicad-retrata.yml)).
- [LICENSES](./LICENSES): textos completos de las licencias.

## Fabricación

piruetas vende chufe armado y probado.

Como es hardware de código abierto, los archivos fuente de KiCad, los archivos de fabricación de [hardware/chufe-v-0-rev-b-fab](./hardware/chufe-v-0-rev-b-fab), los de armado de [hardware/chufe-v-0-rev-b-pcba](./hardware/chufe-v-0-rev-b-pcba) y la [Bill of materials](https://piruetas.xyz/chufe/#bill-of-materials-v01-rev-b) están publicados para que cualquiera pueda estudiar, modificar y fabricar el diseño. piruetas no da soporte para unidades fabricadas o armadas por terceros.

## Créditos

- Aarón Montoya-Moraga: investigación, esquemático, PCB, fabricación y documentación.
- Matías Serrano: revisor experto de esquemáticos y PCBs.

## Licencia

chufe es (c) 2026 piruetas SpA / Aarón Montoya-Moraga.

- Hardware (`hardware/`): [CERN-OHL-P-2.0](./LICENSES/CERN-OHL-P-2.0.txt).
- Documentación (`docs/`): [CC-BY-SA-4.0](./LICENSES/CC-BY-SA-4.0.txt).
- El nombre, logo y marca de piruetas no están cubiertos por estas licencias: ver [LicenseRef-piruetas-branding](./LICENSES/LicenseRef-piruetas-branding.txt).

Ver [LICENSE.md](./LICENSE.md) para los detalles. El repositorio sigue la especificación [REUSE](https://reuse.software/).
