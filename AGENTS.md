# Retningslinjer for AI-agenter (AGENTS.md)

Dette dokument angiver regler og retningslinjer for sprog, formatering og sikkerhed, som AI-assistenter og agenter skal overholde, når der arbejdes på dette repository.

---

## 1. Sprog og tone

- Alt projektmateriale, herunder dokumentation, noter, kommentarer og oversigter, skal skrives på **dansk**.
- Vær kortfattet og præcis. Undgå fyldtekst og overflødige gentagelser.
- Spred information logisk: Overfyld ikke et enkelt dokument. Opret i stedet dedikerede del-dokumenter (f.eks. HARDWARE.md, ARCHITECTURE.md) ved behov, og henvis med relative links.

---

## 2. Formatering og stil

- Links: Brug altid relative stier til filer i repositoriet (f.eks. `[Hardware](HARDWARE.md)`). Brug aldrig absolutte stier eller lokale protokoller som file-links, da koden publiceres på GitHub.
- Tegnsætning: Brug ikke tankestreger som em-dash eller en-dash. Brug udelukkende almindelig bindestreg (-).
- Emojis: Brug ikke emojis i dokumentationen eller kildekoden.
- Typografi: Brug fed skrift med måde og kun til centrale nøgleord eller tabeloverskrifter.

---

## 3. Sikkerhed og hemmeligheder

Dette repository er tiltænkt offentliggørelse på GitHub.
- Tilføj eller commit **aldrig** følsomme oplysninger:
  - Wi-Fi SSID og adgangskoder.
  - API-nøgler, tokens eller adgangskoder til databaser/servere.
  - Private IP-adresser, domæner eller personhenførbare data.
- Eksempel-konfigurationer skal altid anvende pladsholdere (f.eks. `WIFI_SSID="DitNetvaerk"` og `WIFI_PASS="DinKode"`).
