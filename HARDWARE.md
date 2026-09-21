# Hardware-specifikation og overvejelser

## 1. Driftsprincip og strømprofil

- Lyd (dagdrift): Optager lyd i dagtimerne (fra 1 time før solopgang til 1 time efter solnedgang). ESP32 kører ved reduceret clock-frekvens (80 MHz) for at minimere forbrug (~25-35 mA under I2S-optagelse).
- Kamera (hændelsesstyret): Kameraet tændes kun, når PIR-sensoren registrerer bevægelse på brættet. Der tages 3-5 billeder i serie, som gemmes i PSRAM og sendes til serveren sammen med den seneste lydfil.
- Nat (deep sleep): Om natten går enheden i deep sleep (< 20 uA) og vækkes automatisk via RTC-timeren 1 time før solopgang.

---

## 2. Bill of Materials (BOM) pr. enhed

| Ref | Komponent | Model / Varebetegnelse | Funktion | Antal | Ca. pris (DKK) |
| :--- | :--- | :--- | :--- | :---: | :---: |
| U1 | Mikrocontroller | Seeed Studio XIAO ESP32-S3 Sense (eller ESP32-S3-CAM N8R8) | ESP32-S3, 8MB PSRAM, Wi-Fi/BLE, USB-C | 1 | 90 - 120 kr. |
| CAM1 | Billedsensor | OV2640 eller OV5640 | 2 MP / 5 MP DVP kamerasensor | 1 | Inkl. i U1 |
| LENS1 | Objektiv | Justerbar M12 vidvinkellinse (ca. 120 grader) | Manuel fokus justeret til 15-25 cm nærfokus | 1 | 15 - 25 kr. |
| MIC1 | Digital mikrofon | Indbygget PDM-mikrofon på XIAO Sense (eller INMP441 I2S) | Kontinuerlig optagelse af fuglesang | 1 | Inkl. i U1 / 15 kr. |
| SEN1 | Bevægelsessensor | AM312 Mini PIR | Vækker kamerasløjfen ved fuglebesøg (< 20 uA standby) | 1 | 10 - 15 kr. |
| BAT1 | Batteri | 2x 18650 Li-ion celler (parallelt, 3.7V) | 5000-6000 mAh samlet kapacitet | 2 | 60 - 90 kr. |
| PV1 | Solcellepanel | 5V / 3W - 5W monokrystallinsk | Vejrbestandig, dimensioneret til dagtidsdrift | 1 | 45 - 70 kr. |
| CHG1 | Ladekredsløb | CN3791 (MPPT) eller TP4056 med beskyttelse | Opladning fra solcelle og over-/afladningsbeskyttelse | 1 | 15 - 25 kr. |
| ENC1 | Kabinet | 3D-printet i PETG eller ASA | UV- og vejrbestandigt kabinet | 1 | 45 - 65 kr. |
| MECH1 | Mekanik og tætning | M3 rustfri skruer, silikonepakning, akrylglas | Vejrtætning mod regn og fugt | 1 sæt | 20 - 30 kr. |
| Total | | | | | ~300 - 450 kr. |

---

## 3. Strømberegning: Gråvejrsdage og batterikapacitet

Dagsforbrug ved kontinuerlig lytning (ESP32 ved 80 MHz + I2S + Wi-Fi i bursts til upload):
- Gennemsnitligt strømtræk i dagtimerne: ca. 55-65 mA.
- Sommer (19,5 timer aktiv): ca. 1.170 mAh/dag.
- Forår og efterår (14 timer aktiv): ca. 840 mAh/dag.
- Vinter (9 timer aktiv): ca. 540 mAh/dag.

Batterireserve uden solopladning (2x 18650 med ca. 4.800 mAh reel udnyttelig kapacitet):
- Sommer: ca. 4 dages drift uden sol.
- Forår og efterår: ca. 5-6 dages drift uden sol.
- Vinter: ca. 8-9 dages drift uden sol.

Soludbytte under danske vejrforhold (5W panel):
- Sommer ved overskyet vejr: Diffus stråling giver ca. 600-1.000 mAh/dag. Batteriet taber kun 200-500 mAh/dag, hvilket giver op til 10-14 dages tolerance over for dårligt vejr.
- Vinter (november til januar): Solindstrålingen er så lav, at et 5W panel på gråvejrsdage genererer under 100 mAh/dag. Batteriet løber tør efter 8-10 dage uden supplerende opladning.

Anbefalet optimering:
- Brug audio activity detection (VAD): Tænd kun Wi-Fi i korte bursts (5-10 sekunder) ved konstateret lyd eller i faste tidsintervaller. Dette sænker dagsforbruget til ca. 30 mA og fordobler driftstiden på batteri.

---

## 4. Tidsestimat (i timer)

Forventet arbejdstid for en fungerende prototype (MVP):

| Opgave | Estimeret tid | Noter |
| :--- | :--- | :--- |
| 1. Hardware-prototyping på breadboard | 6 - 8 timer | Forbind ESP32, PIR-vækning, kamera og mikrofon. |
| 2. Firmware (PlatformIO / ESP-IDF) | 14 - 18 timer | Deep sleep, PIR-trigger, billedoptagelse til PSRAM og HTTP/MQTT-upload. |
| 3. Servermodtagelse (backend) | 6 - 10 timer | REST endpoint til modtagelse af billeder, lyd og metadata. |
| 4. 3D-print og mekanisk samling | 8 - 12 timer | Print i PETG, montering af pakninger og manuel fokusering af linse. |
| 5. Strømstyring og felttest | 6 - 8 timer | Måling af dvalestrøm og test af Wi-Fi rækkevidde. |
| Total arbejdstid | 40 - 56 timer | Realistisk inden for en uges dedikeret fuldtidsarbejde. |
