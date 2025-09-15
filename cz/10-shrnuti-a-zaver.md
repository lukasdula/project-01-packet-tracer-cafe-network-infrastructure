# **10 - Shrnutí a závěr**


## Závěrečné zhodnocení

Projekt ukazuje kompletní proces návrhu, konfigurace, zabezpečení a testování malé podnikové sítě v simulátoru **Cisco Packet Tracer**. Zahrnuli jsme zásadní funkce vycházející z **CCNA I** vhodné pro projekt, které jsou pro zvolené téma/model klíčové pro vybudování funkční a zabezpečené sítě. 

Od počáteční topologie přes detailní adresní plán, VLAN segmentaci a směrování, až po NAT/PAT a DN služby byla vytvořena funkční síťová infrastruktura pro menší podnik kavárny. 

Díky aplikovaným bezpečnostním opatřením (Port Security, ACL, vypnutí portů) je síť odolná vůči běžným lokálním hrozbám. Průběžné testování a troubleshooting potvrdily, že konfigurace splňuje námi stanovené cíle a může sloužit jako dokončený vzor pro výukové i praktické účely.


## Přehled hlavních kroků projektu


- **Kapitola 1:** Návrh topologie sítě s centrálním routerem R1, hraničním routerem R2 a serverem simulujícím internet. Popis použitého hardwaru a fyzických propojení.
    
- **Kapitola 2:** Adresní a VLAN plánování - statická IP adresace, rozdělení sítě do VLAN 10–40, příprava pro Router-on-a-Stick.
    
- **Kapitola 3:** Základní konfigurace - pojmenování zařízení, statické IP adresy na routerech a PC, propojení R1 ↔ R2.
    
- **Kapitola 4:** Konfigurace VLAN a subrozhraní – vytvoření VLAN, přiřazení portů, nastavení trunku, konfigurace subrozhraní na R1 a ověření konektivity mezi VLANami.
    
- **Kapitola 5:** NAT a PAT - konfigurace statického směrování mezi R1 a R2, nastavení NAT/PAT na R1 pro odchozí provoz VLAN přes jednu veřejnou IP.
    
- **Kapitola 6:** Internet a DNS - propojení s DNS/HTTP serverem, přidání DNS záznamů, ověření funkčnosti překladu domén a načtení webové stránky.
    
- **Kapitola 7:** Zabezpečení sítě - nastavení hesel a uživatelských účtů, varovné bannery, Telnet zabezpečení, Port Security, vypnutí nepoužívaných portů, ACL pro řízení komunikace mezi VLAN.
    
- **Kapitola 8:** Testování konektivity - ověření propojení routerů, VLAN komunikace, funkčnosti NAT/PAT, dostupnosti DNS/HTTP a platnosti bezpečnostních opatření.
    
- **Kapitola 9:** Troubleshooting - řešení tří chybových scénářů (špatné VLAN ID, NAT/PAT na nesprávném rozhraní, pořadí pravidel v ACL) včetně diagnostiky, opravy a ověření.

---

Zpět na přehled projektu: [README](README.cs.md)
