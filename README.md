# Opdracht_Security_Vereisten
Herexamen Software Security: Opdracht Security Vereisten
# Data Flow Diagram

![DataflowDiagram](https://user-images.githubusercontent.com/64362709/183143926-2d57c41d-bb78-49bf-a97a-3b9b094365c9.jpg)

# Toegangsregels

## Admin

- Als admin kan ik inloggen.
- Als admin kan ik uitloggen.
- Als admin kan ik een gebruiker aanmaken.
- Als admin kan ik een gebruiker bijwerken.
- Als admin kan ik een gebruiker verwijderen.
- Als admin kan ik het saldo van gebruikers updaten
- Als admin kan ik de logs bekijken.

## Cashier

- Als cashier kan ik inloggen.
- Als cashier kan ik uitloggen.
- Als cashier kan ik de sale statistieken bekijken.
- Als cashier kan ik een winkelmandje aanvullen.
- Als cashier kan ik een winkelmandje leegmaken.

## Loaner

- Als loaner kan ik inloggen.
- Als loaner kan ik uitloggen.
- Als loaner kan ik items gaan uitlenen.
- Als loaner kan ik items gaan retourneren.
- Als loaner kan ik zien wat er uitgeleend is en aan wie het uitgeleend is en wanneer het uitgeleend is.

## Registration

- Als registration kan ik inloggen.
- Als registration kan ik uitloggen.
- Als registration kan ik het saldo van gebruikers updaten.
- Als registration kan ik een nieuwe gebruiker gaan registreren.

# Stride Analyse
Enkele zaken die mogelijk zijn binnen het RFID System: Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege, Insiders en Bot attacks.

# Classificatie security risico's
Still in progress !!!

# Aanbevelingen
Ik zou aanraden voor de webapp en api te hosten via Azure en gebruikmaken van de db in Azure. Waarom Azure? Zij bieden een tal van functionaliteiten om je web toepassing goed te beveiligen en goed te onderhouden.

## Spoofing
### Probleem?
Een persoon of programma doet zich voor als iemand anders. Brute force attacks.
### Waar?
Webapp
### Oplossing?
Gebruikmaken van Azure AD Multi-Factor Authentication. Dit zorgt ervoor dat je meerdere verificatiemethoden kan gebruiken om te gaan inloggen in je webapp. Dus je kan voorzien dat er alleen ingelogd kan worden met een EhB account.

## Tampering
### Probleem?
SQL injections waardoor aanpassingen aangebracht worden zonder dat men dit wil. Cross-site scripting is dus een aanval met code injection aan de client-side. De aanvaller probeert kwaadaardige scripts uit te voeren in de webbrowser van de gebruiker door kwaadaardige code op te nemen in een legitieme webpagina of webapp. De aanval vindt plaats wanneer de gebruiker de webpagina of webapp bezoekt die de kwaadaardige code uitvoert.  
### Waar?
Webapp, API en DB
### Oplossing?
Gebruikmaken van SQL Threat Detection binnen Azure. Dit zorgt ervoor dat het bedreigingen detecteert waardoor je erop kan reageren zodra die zich voordoen door beveiligingswaarschuwingen te geven over die afwijkende activiteiten. Encryptie van data in transit. Bij cross-site scripting ervoor zorgen dat je geen onbetrouwbare gegevens in uw html-invoer plaatst. Als u niet vertrouwde gegevens toch plaats in uw html zorg er dan voor dat ze encoded zijn binnen uw html. Vooraleer je ook niet vertrouwde data in een url query string plaatst zorg dan ook voor dat ze encode is in uw url.

## Repudiation
### Probleem?
Een bepaalde actie die uitgevoerd is binnen het systeem waarbij men ontkent dat hij/zij dit uitgevoerd heeft. 
### Waar?
Webapp
### Oplossing?
Monitoring op Azure als bepaalde zaken uitgevoerd worden. Non-Repudiation dus ervoor zorgen dat aankopen een signatuur bevat bv: een pdf met de aankoop en daarop de signatuur van beide personen zodat de aankoop wel degelijk gebeurd is.

## Information Disclosure
### Probleem?
Blootleggen van gevoelige data waarbij iemand niet geautoriseerd is om dit te zien.
### Waar?
Webapp, API en DB
### Oplossing?
Rollen gaan toekennen aan de gebruikers van de webapp (admin, cashier, loaner en registration). Zorg ervoor dat data die verstuurd wordt op het netwerk geëncrypteerd wordt. Zoveel mogelijk generieke foutmeldingen geven zodat aanvallers niet onnodige aanwijzingen ontdekken. Hardcoded credentials uit de toepassing halen. Debugging afsluiten zodat de aanvaller geen informatie kan zien van het gedrag van de webapp. Gebruikmaken van TLS.

## Denial of Service
### Probleem?
De website overspoelen met verkeer totdat de webapp crasht of niet meer reageert. 
### Waar?
Webapp, API en DB
### Oplossing?
Gebruikmaken van de Azure DDos Protection. Deze functie zorgt ervoor dat continue monitoring is en automatische beperkingen van netwerkaanvallen.

## Elevation of Privilege
### Probleem?
Probleem: Door dit kan het zijn dat een geautoriseerde of niet geautoriseerde gebruiker(s) in het systeem toegang krijgt tot andere informatie die hij/zij niet mag zien. 
### Waar?
Webapp
### Oplossing?
Rollen gaan toekennen aan bepaalde acties die een gebruiker mag uitvoeren. Azure AD Multi-Factor Authentication dit zorgt ervoor dat je meerdere verificatiemethoden kan gebruiken om te gaan inloggen in de webapp. Waardoor de ingelogde gebruikers hun rol gaan hebben (admin, cashier, loaner of registration).

## Insiders
### Probleem?
Huidige werknemer of voormalige werknemer die toegang heeft tot de gevoelige data en dit misbruikt. 
### Waar?
Webapp, API en DB
### Oplossing?
Gebruikmaken van Microsoft Purview Insider Risk Management. Helpt om interne risico’s te minimaliseren door u in staat te stellen van kwaadaardige en opzettelijke activiteiten in uw organisatie op te sporen, te onderzoeken en erop te reageren.

## Bot attacks
### Probleem?
Gebruik van geautomatiseerde web requests om een website, applicatie, API of eindgebruikers te manipuleren, te bedriegen of te verstoren. 
### Waar?
Webapp en API
### Oplossing?
Azure Web Application Firewall service die een bescherming aanbiedt tegen webhackingtechnieken, zoals SQL injection en beveiligingsproblemen als site-overschrijdende scripts.
