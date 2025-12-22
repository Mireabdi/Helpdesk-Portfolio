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


## 2. OU-rakenne(Organizational Units)

- Domainiin luotiin erilliset OU:t käyttäjille, ryhmille, työasemille ja IT-hallinnalle
- Rakenne mahdollistaa selkeän hallinnan ja myöhemmän ryhmäkäytäntöjen kohdistamisen
- OU:t luotiin PowerShellillä Domain Controllerilla

![ou-created](Screenshots/07-ou-created.png)
![get-adorganizationalunit](Screenshots/08-get-adorganizationalUnit.png)

## 3. Käyttäjät ja ryhmät

- Luotiin domain-käyttäjät IT-hallintaa ja peruskäyttöä varten
- Luotiin globaalit turvaryhmät käyttöoikeuksien hallintaan
- Käyttäjät sijoitettiin OU:ihin (IT, Corp-Users) ja lisättiin ryhmiin

![newuser-adm](Screenshots/09-newuser-adm.png) ![newuser-user1](Screenshots/10-newuser-user1.png) ![newuser-user2](Screenshots/11-newuser-user2.png) ![groups-created](Screenshots/12-groups-created.png) ![addusers-to-group](Screenshots/13-addusers-to-group.png) ![groups-membership](Screenshots/14-groups-membership.png)





  

