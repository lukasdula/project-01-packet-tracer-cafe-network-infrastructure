

# Síťová infrastruktura pro malou kavárnu

## Úvod a cíle

Tento projekt představuje návrh, konfiguraci a testování malé podnikové sítě pro kavárnu.  
Hlavním cílem je vytvořit funkční, oddělené a bezpečné prostředí pro dvě části provozu:

- **Interní síť zaměstnanců** - přístup k hlavnímu počítači (pokladní systém) a interním zařízením kavárny (router, modem, switch) a možnost správy zákaznických počítačů.
    
- **Veřejná síť pro zákazníky** - přístup přes tři veřejné počítače s připojením k internetu a bez možnosti vstupu do interní sítě.
    

Síť byla nastavena ručně v prostředí **Cisco Packet Tracer** pomocí rozhraní CLI. Přenosy jsou oddělené pomocí **VLAN**, propojení mezi routerem a switchem je řešeno metodou **Router-on-a-Stick**.  
Pro simulaci připojení k internetu byl nakonfigurován **NAT/PAT** směrem k routeru R2, který zastupuje poskytovatele internetu. Součástí je také základní serverová infrastruktura (HTTP/DNS) pro testy konektivity.  
Síť je zabezpečena pomocí **hesel pro přístup k zařízení**, **oddělení VLAN** a **omezení přístupu mezi segmenty**, což zajišťuje bezpečný provoz a ochranu před neoprávněným přístupem.

## Struktura projektu (kapitoly)

1. [Síťová topologie a použitá zařízení](01-sitova-topologie-a-pouzita-zarizeni.md)
2. [Adresní a VLAN plánování](02-adresni-a-vlan-planovani.md)
3. [Základní sítová konfigurace](03‑zakladni-sitova-konfigurace.md)
4. [VLANy a subinterface](04-vlany-a-subinterface.md)
5. [NAT a PAT](05-nat-a-pat.md)
6. [Internet a DNS](06-internet-a-dns.md)
7. [Zabezpečení sítě](07‑zabezpeceni‑site.md)
   - Lokální uživatel a heslo pro privilegovaný režim  
   - Varování při přihlášení (MOTD banner)  
   - Zabezpečení Telnet přístupu (VTY lines)  
   - Port Security na zákaznických portech  
   - Administrativní vypnutí nepoužívaných portů  
   - Základní ACL pro omezení provozu mezi VLANami  
8. [Testování konektivity](08‑testovani‑konektivity.md)
9. [Řešení problémů](09‑reseni-problemu.md)
   - 9.1 Nesprávné přiřazení VLAN ID na subinterface  
   - 9.2 NAT/PAT neprovádí překlad kvůli overload na špatném rozhraní  
   - 9.3 ACL - chybné pořadí pravidel blokující komunikaci  
10. [Shrnutí a závěr](10-shrnuti-a-zaver.md)

## Přístup do CLI zařízení

Pro ukázkové účely byly nakonfigurovány přihlašovací údaje k síťovým zařízením. Tyto údaje umožňují vstup do CLI a následně do privilegovaného režimu:

Uživatelské jméno (console + Telnet): `cafeadmin`

Uživatelské heslo: `Espresso25`

Enable secret (privilegovaný režim): `Arabickashot25`

Pro účely projektu jsou zvolena jednodušší tematická hesla. V reálném nasazení by byla použita komplexnější a delší hesla (12+ znaků, kombinace velkých/malých písmen, číslic a speciálních znaků).

## Použité nástroje

- Cisco Packet Tracer (verze 8.2+) – simulace síťového prostředí
    
- Visual Studio Code / Obsidian – psaní a úprava dokumentace
    

## Jak spustit projekt

1. Otevři `.pkt` soubor v Cisco Packet Traceru (8.2+).
    
2. Postupuj podle složek projektu `01–10`.    

## Klíčové funkce projektu

- Statické IP adresy a jasná struktura VLAN
    
- Router-on-a-Stick konfigurace
    
- NAT/PAT pro přístup k simulovanému internetu
    
- HTTP a DNS server pro testování
    
- Základní síťové zabezpečení
    
- Simulované chyby a jejich řešení v části Troubleshooting


## Poznámka autora

Tento projekt je součástí mého **studijního portfolia** a praktické přípravy na kurz **CCNA I**.  
Při tvorbě jsem si osvojil klíčové principy síťování, od plánování a adresace přes konfiguraci až po diagnostiku a opravy.

Nejvíc mě bavilo budování funkční sítě od úplného základu až po celek s jasným řádem a pravidly, od práce s **VLANami**, kdy síť po konfiguraci začala mezi sebou správně komunikovat, až po **komplexní zabezpečení sítě** a zavedení bezpečnostních zásad.  
Věřím, že tahle práce může být inspirací i pro další zájemce o sítě nebo lidi, které tohle téma baví.

Síťařina pro mě není jen soubor příkazů, ale i prostor pro tvořivost a logické myšlení.  
Největší odměnou je pro mě ten pocit, kdy po dlouhých hodinách nastavování a ladění vidím, že síť funguje čistě, zabezpečená a bez chyb.

© 2025 – Lukáš Dula | Domácí síťový lab & portfolio
