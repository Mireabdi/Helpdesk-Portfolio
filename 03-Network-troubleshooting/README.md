# 03-network-troubleshoot
### Abdirahman Mire

# 03 DNS & DHCP

## Yleiskuvaus

Tässä projektissa toteutetaan ja vianmäärityksen kautta validoidaan Windows-ympäristön perusverkkopalvelut (DNS ja DHCP). Projekti on rakennettu helpdesk-näkökulmasta ja keskittyy yleiseen domain-ympäristön ongelmaan: työasema ei pysty resolvoimaan domain-resursseja väärän DNS-konfiguraation vuoksi.

Projekti sisältää suunnitellun virhetilanteen, systemaattisen vianmäärityksen sekä korjauksen ja testauksen.

## Ympäristö

### Virtuaaliympäristö: VMware Workstation (NAT)
- Domain Controller: Windows Server 2022 Server Core
- Hostname: DC01
- Roolit: AD DS, DNS, DHCP
- Domain: mire.local

### Client-työasema:

- Windows 11 Pro (Mire-PC)
- RSAT asennettu
- Verkko: IPv4 / DHCP

## Projektin tavoite

- Toteuttaa toimiva DNS- ja DHCP-ympäristö Active Directory -domainissa
- Varmistaa, että työasema saa oikeat verkkoasetukset DHCP:ltä
- Todentaa dynaaminen DNS-rekisteröityminen
- Simuloida ja ratkaista yleinen helpdesk-tason verkko-ongelma
- Dokumentoida koko prosessi selkeästi ja toistettavasti

  
