# 04 File Services – NTFS & Share Permissions
### Abdirahman Mire

## Yleiskuvaus
Tässä projektissa toteutetaan File Services -kokonaisuus Active Directory -ympäristössä helpdesk-näkökulmasta. Projekti keskittyy SMB-jaon luontiin sekä NTFS- ja Share-oikeuksien hallintaan ryhmäpohjaisesti Server Core -ympäristössä.

Tavoitteena on rakentaa selkeä ja tuotantoympäristöä vastaava käyttöoikeusmalli, jossa jaon näkyvyys ja varsinaiset käyttöoikeudet on erotettu toisistaan.

## Ympäristö
- Domain Controller / File Server: DC01  
- Käyttöjärjestelmä: Windows Server 2022 Server Core  
- Domain: mire.local  
- Client-työasema: Windows 11 Pro (domainiin liitetty)  
- Hallinta: RSAT (client-työasemalta)  
- Verkko: IPv4 / DHCP  

---

## Projektin tavoite
- Toteuttaa SMB-tiedostojako domain-ympäristössä  
- Hallita käyttöoikeudet ryhmäpohjaisesti (ei käyttäjäkohtaisia oikeuksia)  
- Erotella Share- ja NTFS-oikeuksien vastuut  
- Rakentaa pohja tyypilliselle käyttöoikeuksiin liittyvälle helpdesk-caselle  

## 1. SMB-jaon luonti
Domain controllerille luotiin jaettava resurssi osastokohtaista tiedostojen hallintaa varten.

Kansio jaettiin verkkoon SMB-jakona nimellä **Departments**.  
Jaon toiminta validoitiin sekä palvelimella että domainiin liitetyllä työasemalla.

![kansiorakenne](screenshots/01-kansiorakenne.png)  
![kansiorakenne](screenshots/02-kansiorakenne-2.png)  
![smb-share-created](screenshots/03-get-smbshare.png)

## 2. Ryhmät ja käyttöoikeusmalli
Käyttöoikeudet toteutettiin ryhmäpohjaisesti Active Directory -ryhmiä hyödyntäen.

Luodut ryhmät:
- HR_RW  
- IT_RW  

Oikeudet myönnetään ainoastaan ryhmille, ei yksittäisille käyttäjille.

![ad-groups](screenshots/05-groups.png)

## 3. Share-oikeudet
Share-oikeudet pidettiin yksinkertaisina ja niitä käytettiin vain jaon yleiseen näkyvyyteen.

- Authenticated Users: Read  
- Administrators: Full Control  

Varsinainen käyttöoikeuksien hallinta toteutettiin NTFS-oikeuksilla.

![share-permissions](screenshots/06-share-permissions-department.png)

## 4. NTFS-oikeudet
NTFS-oikeudet määritettiin osastokohtaisiin alikansioihin.

**Departments (juurikansio):**
- Periytyvät oikeudet pidettiin käytössä näkyvyyttä varten  

**HR-kansio:**
- HR_RW: Modify  
- Administrators: Full Control  
- SYSTEM: Full Control  

**IT-kansio:**
- IT_RW: Modify  
- Administrators: Full Control  
- SYSTEM: Full Control  

NTFS-oikeudet määritettiin domainiin liitetyltä työasemalta RSAT-työkaluilla, koska tiedostopalvelin toimii Server Core -ympäristössä ilman graafista käyttöliittymää.

![ntfs-departments](screenshots/07-ntfs-permissions-department.png)  
![ntfs-hr](screenshots/09-ntfs-permissions-hr.png)  
![ntfs-it](screenshots/08-ntfs-permissions-it.png)
