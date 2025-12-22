# 02 Active directory

#### Abdirahman Mire

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

![sconfig-rename](Screenshots/01-sconfig-rename.png) 
![ipconfig-all](Screenshots/02-ipconfig-all.png)
![feature-installed](Screenshots/03-feature-installed.png)
![install-addsforest](Screenshots/04-install-addsforest.png)
![get-addomain](Screenshots/05-get-addomain.png) 
![addforest](Screenshots/06-get-addforest.png)


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

![newuser-adm](Screenshots/09-newuser-adm.png)
![newuser-user1](Screenshots/10-newuser-user1.png)
![newuser-user2](Screenshots/11-newuser-user2.png)
![groups-created](Screenshots/12-groups-created.png)
![addusers-to-group](Screenshots/13-addusers-to-group.png) 
![groups-membership](Screenshots/14-groups-membership.png)

## 4. Työaseman liittäminen domainiin

- Windows 11 -työasema liitettiin domainiin `mire.local`
- Työasema konfiguroitiin käyttämään Domain Controlleria DNS-palvelimena
- Olemassa oleva tietokonetili hyödynnettiin domain joinissa
- Domain-käyttäjällä kirjautuminen testattiin onnistuneesti

![client-dns](Screenshots/15-client-dns.png)
![domain-admins-membership](Screenshots/16-domain-admins-membership.png)
![domain-user-login](Screenshots/17-domain-user-login.png)
![domain-member](Screenshots/18-domain-member.png)
![ad-computer-object](Screenshots/19-ad-computer-object.png) 


## 5. Group Policy (GPO)

- Luotiin GPO GPO-Workstation-Restrictions
- GPO hallittiin RSAT-työkaluilla domainiin liitetyltä työasemalta
- Käytäntö estää Control Panelin ja PC-asetusten käytön peruskäyttäjiltä
- GPO linkitettiin käyttäjien OU:hun

![gpo-created](Screenshots/20-gpo-created.png)
![gpo-created2](Screenshots/23-gpo-created2.png)
![gpo-setting](Screenshots/21-gpo-setting.png)
![gpo-setting](Screenshots/22-gpo-test.png)

## 6. Helpdesk-case: käyttäjätilin lukitus (hallittu)

#### Tilanne:

- Käyttäjä ei pääse kirjautumaan domainiin. Kirjautumisyritys palauttaa virheilmoituksen, että käyttäjätili on lukittu.

#### Diagnoosi:
- Active Directoryn Account Lockout Policy lukitsi käyttäjätilin useiden epäonnistuneiden kirjautumisyritysten jälkeen.

#### Toimenpiteet:

- Domainiin määritettiin Account Lockout Policy lukituskynnyksellä
- Käyttäjätilin lukitustila varmistettiin Active Directory Users and Computers -konsolissa
- Lukitus vapautettiin poistamalla Unlock account -valinta
- Kirjautuminen testattiin uudelleen työasemalla

#### Lopputulos:
Käyttäjä pystyi kirjautumaan domainiin normaalisti lukituksen vapauttamisen jälkeen.

![policy](Screenshots/26-policy.png)
![account-locked](Screenshots/24-account-locked.png)
![account-unlocked](Screenshots/25-account-unlocked.png)
![login-success](Screenshots/27-login-success.png)


## Helpdesk-yhteys (Active Directory)

Tässä kokonaisuudessa toteutettiin Active Directory -ympäristö helpdesk-näkökulmasta. Työ kattoi Domain Controllerin käyttöönoton, OU-rakenteen, käyttäjä- ja ryhmähallinnan, työaseman liittämisen domainiin sekä Group Policy -hallinnan RSAT-työkaluilla. Lisäksi simuloitiin hallittu helpdesk-case, jossa käyttäjän kirjautumisongelma johtui lukittuneesta käyttäjätilistä ja ratkaistiin Active Directoryn avulla.





