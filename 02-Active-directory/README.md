# 02-active-directory


## Tavoite

Tämän projektin tavoitteena on toteuttaa Active Directory -ympäristö helpdesk-näkökulmasta. Projekti kattaa Domain Controllerin käyttöönoton, perusrakenteen (OU), käyttäjä- ja ryhmähallinnan, työaseman liittämisen domainiin sekä tyypillisen helpdesk-vikatilanteen.

### Ympäristö:

- Virtuaaliympäristö: VMware Workstation
- Domain Controller: DC01
- Käyttöjärjestelmä: Windows Server 2022 Server Core
- Domain: mire.local
- NetBIOS: MIRE
- Verkko: Host-only
- IP-osoite: Staattinen (DC01 osoittaa DNS:llä itseensä)

## 1. Domain Controllerin käyttöönotto

- Palvelin nimettiin DC01 ja verkko määritettiin staattiseksi
- DNS-palvelimeksi asetettiin palvelimen oma IP-osoite
- Active Directory Domain Services- ja DNS-roolit asennettiin
- Luotiin uusi forest ja domain mire.local

![sconfig-rename](Screenshots/01-sconfig-rename.png) ![ipconfig-all](Screenshots/02-ipconfig-all.png) ![feature-installed](Screenshots/03-feature-installed.png) ![install-addsforest](Screenshots/04-install-addsforest.png) ![get-addomain](Screenshots/05-get-addomain.png) ![addforest](Screenshots/06-get-addforest.png)


## 1. OU-rakenne(Organizational Units)

- Domainiin luotiin erilliset OU:t käyttäjille, ryhmille, työasemille ja IT-hallinnalle
- Rakenne mahdollistaa selkeän hallinnan ja myöhemmän ryhmäkäytäntöjen kohdistamisen
- OU:t luotiin PowerShellillä Domain Controllerilla

![ou-created](Screenshots/07-ou-created.png)
![get-adorganizationalunit](Screenshots/08-get-adorganizationalUnit.png)


  

