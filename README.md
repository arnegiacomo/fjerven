# Fjerven

Et gør-det-selv smart foderbræt med kamera og mikrofon inspireret af Bird Buddy. Enheden registrerer fuglebesøg, tager en serie billeder og optager lyd, og videresender data til en central server til artsgenkendelse og statistik.

---

## Vision (Specifikation)

> Jeg vil have et smart foderbræt, der optager fuglesang og tager billeder ved besøg, så jeg kan kortlægge fuglene omkring mit hus, følge med i besøgstal fordelt på dage, uger, måneder og år, skelne mellem hørte og sete fugle, og i sidste ende se fugleforekomster på tværs af Danmark.

---

## Arkitektur og dokumenter

- [Hardware og komponenter](HARDWARE.md): Komponentliste, stykliste (BOM), strømberegninger og tidsestimat.
- Server og genkendelse: (Kommende) Billed- og lydlagring, artsgenkendelse og kortvisning.
- OTA (Over-the-Air Updates): (Kommende) Fjernopdatering af firmware via server/Wi-Fi.

---

## Illustrationer og visuel identitet

Til præsentation og artskort anvendes illustrationer fra:
- [fugleramme](https://github.com/arnegiacomo/fugleramme) af Arne Giacomo Munthe-Kaas.

---

## Udviklingsværktøjer

- PlatformIO / ESP-IDF i VS Code (firmware til ESP32-S3)
- KiCAD (eventuelt printudlæg)
- 3D-printer slicer (f.eks. PrusaSlicer eller Bambu Studio til PETG/ASA-kabinet)
- FreeCAD
