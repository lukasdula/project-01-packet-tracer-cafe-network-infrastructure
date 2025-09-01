# **2 – Adresní a VLAN plánování**


## 2.1 – Úvod

V této kapitole stanovíme logické rozdělení sítě, přiřadíme statické IP adresy a VLAN jednotlivým zařízením.  
Cílem je síť uspořádat, rozdělit do oddělených, bezpečných segmentů pro zaměstnance i zákazníky a vytvořit WAN propojení směrem k simulovanému poskytovateli internetu.


## 2.2 – IP adresace a přehled podsítí

Každé zařízení ve vnitřní síti má staticky přiřazenou IP adresu. Adresy jsou přiděleny dle VLAN, do kterých jednotlivá zařízení spadají. Všechny VLANy využívají masku podsítě /24 (255.255.255.0), což odpovídá běžnému nastavení pro menší a střední podniky.

| Zařízení  | Popis                                     | IP adresa                    | Maska podsítě | Výchozí brána |
| --------- | ----------------------------------------- | ---------------------------- | ------------- | ------------- |
| PC-1      | Zaměstnanci                               | 192.168.10.10                | 255.255.255.0 | 192.168.10.1  |
| PC-2      | Zákazník                                  | 192.168.20.10                | 255.255.255.0 | 192.168.20.1  |
| PC-3      | Zákazník                                  | 192.168.30.10                | 255.255.255.0 | 192.168.30.1  |
| PC-4      | Zákazník                                  | 192.168.40.10                | 255.255.255.0 | 192.168.40.1  |
| Router R1 | Brána do vnitřní sítě                     | 192.168.10.1<br>192.168.99.2 | 255.255.255.0 | 192.168.99.1  |
| Router R2 | Hraniční router simulující ISP            | 192.168.99.1                 | 255.255.255.0 | —             |
|   Server  | Simulace internetových služeb (DNS, HTTP) | 10.10.10.100                 | 255.255.255.0 | 10.10.10.1    |

>**Poznámka:** V tomto návrhu zatím nevyužíváme DHCP server. Cílem je demonstrovat správné manuální přiřazení IP adres. 


## 2.3 – VLAN plánování

Pro účely tohoto projektu využíváme VLAN (Virtual Local Area Network) pro oddělení provozu mezi různými typy zařízení a uživatelů v kavárně. Rozdělení pomocí VLAN zvyšuje bezpečnost, zjednodušuje správu a přispívá k efektivnějšímu směrování provozu v síti.

Každá VLAN bude mít vlastní IP podsíť a bude nakonfigurována na rozhraní routeru pomocí Router-on-a-Stick (subinterfaces).

| VLAN ID | Název VLAN | Popis / účel                 | Přiřazená síť   | Výchozí brána | Přiřazená zařízení |
| ------- | ---------- | ---------------------------- | --------------- | ------------- | ------------------ |
| 10      | Staff-1    | Interní síť zaměstnanců PC-1 | 192.168.10.0/24 | 192.168.10.1  | PC-1, Router R1    |
| 20      | Guest-2    | Zákazník PC-2                | 192.168.20.0/24 | 192.168.20.1  | PC-2               |
| 30      | Guest-3    | Zákazník PC-3                | 192.168.30.0/24 | 192.168.30.1  | PC-3               |
| 40      | Guest-4    | Zákazník PC-4                | 192.168.40.0/24 | 192.168.40.1  | PC-4               |

> Poznámka: R1 je propojen s jednotlivými VLAN přes trunk port a využívá Router-on-a-Stick (subinterfaces). 



## 2.4 – Vysvětlení propojení mezi Router R2 a Router R1

V tomto projektu slouží **Router R2 jako hraniční bod sítě**, který představuje připojení k internetu.  
Je propojen s Routerem R1, který zajišťuje komunikaci v rámci interních VLAN.

R2 směruje provoz ze sítě „poskytovatele“ (např. server s DNS/HTTP) do vnitřní sítě kavárny.  
Naopak R1 odesílá provoz z VLAN směrem ven – přes R2 – k serveru simulujícímu Internet.  
Router R2 **nepoužívá výchozí bránu**, protože simulace končí na serveru – tedy uvnitř vlastní sítě.

---

### 2.5 – Význam NAT/PAT v projektu

- NAT/PAT je nakonfigurován **na Routeru R1**, kde dochází k překladu privátních IP na veřejnou.
    
- R2 přeposílá pakety mezi R1 a serverem bez dalšího překladu.
    
- Statické směrování (`ip route`) je:
    
    - na R1 směrem na R2 (do sítě se serverem),
        
    - na R2 zpět do sítě VLAN (interní síť kavárny).

