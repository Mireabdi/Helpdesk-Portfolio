# 01-workstation-setup

## Tavoite

Tämän projektin tavoitteena oli toteuttaa Windows 11 Pro -työaseman perusasennus ja käyttöönotto helpdesk-näkökulmasta. Projekti kattaa työaseman asennuksen, peruskovennuksen, käyttäjähallinnan, jaetun resurssin, tulostuksen sekä yhden hallitun vikatilanteen ja sen ratkaisemisen.

## Ympäristö

Virtuaaliympäristö: VMware Workstation

Käyttöjärjestelmä: Windows 11 Pro

Verkko: NAT

CPU: 2 core

RAM: 7.8 GB

Levytila: 70GB

## Toteutus

### Windows 11 Pro -asennus

- Windows 11 Pro asennettu puhtaana asennuksena

- Paikallinen admin-käyttäjä luotu

- VMware Tools asennettu

![kuva1](screenshots/01-system-about.png)

![kuva1](screenshots/02-vmware-tools.png)

### 2. Päivitykset ja ajurit

- Päivitykset ajettu loppuun

- Järjestelmä ajan tasalla

- Laitehallinta tarkistettu

![kuva1](screenshots/03-windows-update.png)

![kuva1](screenshots/04-device-manager.png)

### 3. Peruskovennus

- Windows Defender (Real-time protection) käytössä

- Palomuuri käytössä kaikissa profiileissa

- BitLocker ei ollut käytettävissä tässä virtuaaliympäristössä, koska virtuaalikone ei tarjoa täyttä TPM-tukea salaukselle.

![kuva1](screenshots/05-defender.png)

![kuva1](screenshots/06-firewall.png)

![kuva1](screenshots/07-bitlocker-status.png)

### 4. Käyttäjähallinta

- Käyttäjien luonti: loin käyttäjät mire-user ja test-user.

![kuva1](screenshots/08-local-users.png)
![kuva1](screenshots/09-local-users-added.png)

- Paikallinen ryhmä: loin ryhmän Helpdesk-local johon lisäsin käyttäjät mire-user ja test-user.

![kuva1](screenshots/10-Groups.png)
![kuva1](screenshots/11-users-added-to-group.png)

- Käyttöoikeuksien erottelu: tarkistin member of sivulta oikeudet ja varmistin ettei käyttäjillä ollut admin oikeuksia.

  ![kuva1](screenshots/12-member-of-mire-user.png)
  ![kuva1](screenshots/13-member-of-test-user.png)

- Kirjautumistestaus: lopuksi testasin kirjautumista.
  
![kuva1](screenshots/14-login-mire-user.png)
![kuva1](screenshots/15-login-test-user.png)
  


