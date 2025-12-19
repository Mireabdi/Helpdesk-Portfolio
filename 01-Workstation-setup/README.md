# 01-workstation-setup

## Tavoite

Tämän projektin tavoitteena oli toteuttaa Windows 11 Pro -työaseman perusasennus ja käyttöönotto helpdesk-näkökulmasta. Projekti kattaa työaseman asennuksen, peruskovennuksen, käyttäjähallinnan, jaetun resurssin, tulostuksen sekä yhden hallitun vikatilanteen ja sen ratkaisemisen.

## Ympäristö

Virtuaaliympäristö: VMware Workstation

Käyttöjärjestelmä: Windows 11 Pro

Verkko: NAT

Resurssit:
- CPU: 2 cores
- RAM: 8 GB
- Levytila: 70 GB

## Toteutus

### Windows 11 Pro -asennus

- Windows 11 Pro asennettu puhtaana asennuksena
- Tietokone nimetty muotoon `mire-pc`
- Paikallinen admin-käyttäjä luotu
- VMware Tools asennettu

![system-about](screenshots/01-system-about.png)
![vmware-tools](screenshots/02-vmware-tools.png)

### 2. Päivitykset ja ajurit

- Päivitykset ajettu loppuun
- Järjestelmä ajan tasalla
- Laitehallinta tarkistettu

![windows-update](screenshots/03-windows-update.png)

![device-manager](screenshots/04-device-manager.png)

### 3. Peruskovennus

- Windows Defender (Real-time protection) käytössä
- Palomuuri käytössä kaikissa profiileissa
- BitLocker ei ollut käytettävissä tässä virtuaaliympäristössä (VMware / TPM-rajoite)

![defender](screenshots/05-defender.png)
![firewall](screenshots/06-firewall.png)
![bitlocker-status](screenshots/07-bitlocker-status.png)

### 4. Käyttäjähallinta

- Käyttäjien luonti: Luotiin käyttäjät mire-user ja test-user.

![local-users](screenshots/08-local-users.png)
![local-users-added](screenshots/09-local-users-added.png)

- Paikallinen ryhmä: Paikallinen ryhmä Helpdesk-Local luotu ja käyttäjät mire-user ja test-user lisätty ryhmään

![groups](screenshots/10-Groups.png)
![users-added-to-group](screenshots/11-users-added-to-group.png)

- Käyttöoikeuksien erottelu: Tarkistettiin member of sivulta oikeudet ja varmistettiin ettei käyttäjillä ollut admin oikeuksia.

  ![kuva1](screenshots/12-member-of-mire-user.png)
  ![kuva1](screenshots/13-member-of-test-user.png)

- Kirjautumistestaus: lopuksi testattiin kirjautumista.
  
![login-mire-test](screenshots/14-login-mire-user.png)
![login-test-user](screenshots/15-login-test-user.png)

### 5. Jaettu kansio

Tässä vaiheessa toteutettiin jaetun kansion luonti ja käyttöoikeuksien määrittely helpdesk-näkökulmasta.

- Luotiin kansiorakenne C:\Support\PublicDocs

![share-folder](screenshots/16-share-folder.png)

- Kansio jaettiin verkkoon nimellä PublicDocs


Share-oikeudet:

- Everyone: Read
- Helpdesk-Local: Change

![share-settings-1](screenshots/17-share-settings-1.png)
![share-settings-2](screenshots/18-share-settings-2.png)

NTFS-oikeudet:

- Administrators: Full Control
- Helpdesk-Local: Modify
- Users: Read & Execute

![ntfs-permissions-admin](screenshots/19-ntfs-permissions-admin.png)
![ntfs-permissions-helpdesk-local](screenshots/20-ntfs-permissions-helpdesk-local.png)
![ntfs-permissions-users](screenshots/21-ntfs-permissions-users.png)

Testattiin että jaettu kansio toimii: Kirjauduttiin mire-user käyttäjälle ja tallennettiin tekstitiedosto jaettuun kansioon.

![ntfs-permissions-test](screenshots/22-ntfs-permissions-test.png)

### 6. Tulostus(virtuaalinen)

- Tarkistettu, että Microsoft Print to PDF -tulostin on käytettävissä
- Suoritettu testitulostus Notepadista
- Tulostus tallennettu PDF-muotoon polkuun `C:\Support\test-print.pdf`

![print-to-pdf](screenshots/23-print-to-pdf.png)
![test-print-result](screenshots/24-test-print-result.png)


