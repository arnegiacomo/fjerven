# fjerven

En opgradering til fuglehuset DENVER BFC-1200, der udstyrer den med fuglegenkendelse fra billeder og sang (dertil mikrofon). Alt det omkring for at det kan lade sig gøre.

## Enheder

Nedenstående liste giver et hurtigt overblik, men flere detaljer findes under tilhørende overskrift.

- Denver BFC-1200 eller tilsvarende
- ESP32-S3

### Denver BFC-1200 (fuglehus med kamera)

Det er ikke nødvendigt at bruge lige præcis denne model, men det er den, som jeg har anvendt og arbejdet ud fra. Jeg tænker sagtens, at man kan tilpasse, hvad jeg har gjort og lavet til enhver anden løsning. Hvad der findes her, er først og fremmest for den, men jeg vil gerne gøre det så generelt så muligt, så det kan tilpasses.

### ESP32-S3

Det skal bare være en eller anden microcontroller, som

- ikke bruger for meget strøm, da det kører på batteri.
- understøtter USB-OTG.
- understøtter mikrofon.
- understøtter bluetooth (kan også nøjes med wifi, men det æder strøm).


## Værktøjer

Du kan finde nedenfor applikationer nødvendige for at interagere med nogle af filerne.

- KiCAD
- PlatformIO i VSCode

