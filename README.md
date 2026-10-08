# chufe

## About

chufe is an open source hardware Eurorack power supply by [piruetas](https://piruetas.xyz). It takes 12 V DC from a barrel jack, with reverse polarity protection, and outputs ±12V (from a 20 W isolated DC-DC converter) and +5V (from an L7805 linear regulator) on a 16-pin Eurorack power header and a 4-pin Molex KK-396 connector, with an LED for each rail. It is designed to feed a power bus such as [chufebu](https://github.com/piruetasxyz/chufebu). The design is made in KiCad 10 with KiCad's standard libraries plus one third-party part, included in `terceros/`. Hardware is licensed under CERN-OHL-P-2.0 and documentation under CC-BY-SA-4.0 (see [LICENSE.md](./LICENSE.md)). Documentation, schematic, board render and bill of materials (in Spanish): <https://piruetas.xyz/chufe/>.

## Acerca de

Fuente de alimentación eurorack de [piruetas](https://piruetas.xyz), hecha en KiCad y publicada como hardware de código abierto.

Documentación, esquemático, placa y Bill of materials: <https://piruetas.xyz/chufe/>.

## Características

- Entrada de 12 V DC por jack, con protección contra polaridad inversa.
- Salidas de +12V y -12V desde un convertidor DC-DC aislado de 20 W (URA2412YMD-20WR3).
- Salida de +5V desde un regulador lineal L7805, alimentado desde +12V.
- Un header de alimentación Eurorack de 16 pines (2x08) y un conector Molex KK-396 de 4 pines: -12V, GND, +5V y +12V.
- 4 LEDs indicadores: entrada, -12V, +12V y +5V.
- Placa de 50 × 65 mm, 2 capas, con 4 agujeros de montaje M3.
- Hecha para alimentar un bus como [chufebu](https://github.com/piruetasxyz/chufebu).

## Pines y manual de uso

Los pines del header de 16 pines y del conector KK-396, cómo conectar chufe y las advertencias están en el [manual de uso](https://piruetas.xyz/chufe/#manual-de-uso).

## Revisiones

- `v0.1 rev-a`: octubre 2026, todavía sin probar.

## Estructura del repositorio

- [hardware/chufe-v-0-rev-a](./hardware/chufe-v-0-rev-a): proyecto de KiCad (esquemático y placa), los archivos fuente del diseño.
- [hardware/chufe-v-0-rev-a-fab](./hardware/chufe-v-0-rev-a-fab): gerbers y archivos de taladrado para fabricar la placa.
- [hardware/chufe-v-0-rev-a-pcba](./hardware/chufe-v-0-rev-a-pcba): lista de componentes y archivo de posiciones para armado en JLCPCB.
- [terceros](./terceros): símbolo, huella y modelos 3D del convertidor URA2412YMD-20WR3, de la biblioteca de EasyEDA / LCSC / JLCPCB. Van en el repositorio para que el proyecto de KiCad se abra sin instalar bibliotecas adicionales.
- [docs](./docs): documentación, publicada en <https://piruetas.xyz/chufe/>. Las capturas del esquemático y de la placa, y la tabla de Bill of materials, las genera [kicad-retrata](https://github.com/piruetasxyz/kicad-retrata) en cada push (ver [kicad-retrata.yml](./kicad-retrata.yml)).
- [LICENSES](./LICENSES): textos completos de las licencias.

## Fabricación

piruetas vende chufe armado y probado.

Como es hardware de código abierto, los archivos fuente de KiCad, los archivos de fabricación de [hardware/chufe-v-0-rev-a-fab](./hardware/chufe-v-0-rev-a-fab), los de armado de [hardware/chufe-v-0-rev-a-pcba](./hardware/chufe-v-0-rev-a-pcba) y la [Bill of materials](https://piruetas.xyz/chufe/#bill-of-materials-v01-rev-a) están publicados para que cualquiera pueda estudiar, modificar y fabricar el diseño. piruetas no da soporte para unidades fabricadas o armadas por terceros.

## Créditos

- Aarón Montoya-Moraga: investigación, esquemático, PCB, fabricación y documentación.
- Matías Serrano: revisor experto de esquemáticos y PCBs.

## Licencia

chufe es (c) 2026 piruetas SpA / Aarón Montoya-Moraga.

- Hardware (`hardware/`): [CERN-OHL-P-2.0](./LICENSES/CERN-OHL-P-2.0.txt).
- Documentación (`docs/`): [CC-BY-SA-4.0](./LICENSES/CC-BY-SA-4.0.txt).
- El nombre, logo y marca de piruetas no están cubiertos por estas licencias: ver [LicenseRef-piruetas-branding](./LICENSES/LicenseRef-piruetas-branding.txt).
- Componentes de terceros (`terceros/`): el símbolo, la huella y los modelos 3D del convertidor DC-DC URA2412YMD-20WR3 ([LCSC C5369773](https://www.lcsc.com/product-detail/C5369773.html)) vienen de la biblioteca de EasyEDA / LCSC / JLCPCB, convertidos a KiCad con [easyeda2kicad](https://github.com/uPesy/easyeda2kicad.py). No son obra de piruetas ni están cubiertos por estas licencias: ver [LicenseRef-easyeda](./LICENSES/LicenseRef-easyeda.txt).

Ver [LICENSE.md](./LICENSE.md) para los detalles. El repositorio sigue la especificación [REUSE](https://reuse.software/).
