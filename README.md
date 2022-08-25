# Opdracht_Security_Vereisten
Herexamen Software Security: Opdracht Security Vereisten
# Data Flow Diagram

![DataflowDiagram (1)](https://user-images.githubusercontent.com/64362709/186705787-ed838540-48ed-441c-a545-43d4ff07d6f6.jpg)


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

# Stride Analyse

## Spoofing
Het kan zijn dat een persoon of programma zich vooordoet als iemand anders. Brute force attacks. Deze aanval zou binnen de webapplicatie gebeuren. Het gevolg hiervan is dat de aanvaller gaat lopen met iemand zijn credentials. Deze aanval moet aangepakt worden.

## Tampering
Hierbij kunnen er eventuele SQL injections uitgevoerd worden en Cross-Site scripting. Deze aanvallen bevinden zich in webapplicatie, API en DB. Het gevolg hiervan is dat aanvallers de mogelijkheid hebben om: Het lezen van alle gegevens en uitvoeren van willekeurige acties door zich voor te doen als de gebruiker. 

## Repudiation
Een actie wordt uitgevoerd door een aanvaller en ontkent dat hij deze heeft uitgevoerd. Deze aanval bevindt zich in webapplicatie, API en DB. Het gevolg hiervan is dat er actie is uitgevoerd zonder dat men weet wie het gedaan heeft.

## Information Disclosure
Gevoelige data die wordt blootgelegd zonder dat men die rechten heeft om die te bekijken of aan te passen. Deze aanval gebeurt in de webapplicatie, API en DB. Het gevolg ervan is als men geen rollen toekent er gevoelige data wordt blootgelegd en er acties worden uitgevoerd zonder dat men dit wil.

## Denial of Service
De webapplicatie wordt overspoelt met verkeer. De aanval wordt uitgevoerd binnen de webapplicatie, API en DB. Het gevolg hiervan is dat de webapplicatie crasht en niet meer gaat werken.

## Elevation of Privilege
Geautoriseerde en niet geautoriseerde gebruikers krijgen toegang tot informatie die ze niet mogen zien. De aanval heeft betrekking tot de webapplicatie. Het gevolg hiervan is dat gevoelige data wordt blootgelegd aan gebruikers die het recht niet hebben om die te zien.

## Insiders
Het kan zijn dat binnen de organisatie iemand recht heeft om gevoelige data te bekijken en of aan te passen. Met die acties die hij kan gebruiken maakt hij er misbruik van. De aanval heeft betrekking tot de webapplicatie, API en DB. Het gevolg hiervan is dat gevoelige data en acties misbruikt worden door een persoon waardoor dit invloed heeft op het systeem.

## Bot attacks
Het gebruik van geautomatiseerde web requests om een website, applicatie, API of eindgebruikers te manipuleren, te bedriegen of te verstoren. De aanval bevindt zich in de webapplicatie en API. Het gevolg hiervan is dat het systeem gemanipuleert wordt door die requests en zo niet optimaal functioneert.

# Classificatie security risico's
| Threat  | Risk level | Risk option |
| ------------- | ------------- | ------------- |
| Spoofing  | Medium | Aanpakken |
| Tampering  | High | Aanpakken |
| Repudiation  | Low | Aanvaarden |
| Information disclosure  | High | Aanpakken |
| Denial of Service  | High | Aanpakken |
| Elevation of privilege  | Medium | Aanpakken |
| Insiders  | Low | Aanvaarden |
| Bot attacks  | High | Aanpakken |

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
Rollen gaan toekennen aan bepaalde acties die een gebruiker mag uitvoeren. Azure AD Multi-Factor Authentication dit zorgt ervoor dat je meerdere verificatiemethoden kan gebruiken om te gaan inloggen in de webapp. Waardoor de ingelogde gebruikers hun rol gaan hebben (admin, cashier, loaner) door roles te gaan koppelen binnenin Azure AD.

## Insiders
### Probleem?
Huidige werknemer of voormalige werknemer die toegang heeft tot de gevoelige data en dit misbruikt. 
### Waar?
Webapp, API en DB
### Oplossing?
Gebruikmaken van Microsoft Purview Insider Risk Management. Helpt om interne risico’s te minimaliseren door u in staat te stellen van kwaadaardige en opzettelijke activiteiten in uw organisatie op te sporen, te onderzoeken en erop te reageren. Zorg voor een Root User die het systeem opstart en eventuele andere admin zaken kan gaan uitvoeren.

## Bot attacks
### Probleem?
Gebruik van geautomatiseerde web requests om een website, applicatie, API of eindgebruikers te manipuleren, te bedriegen of te verstoren. 
### Waar?
Webapp en API
### Oplossing?
Azure Web Application Firewall service die een bescherming aanbiedt tegen webhackingtechnieken, zoals SQL injection en beveiligingsproblemen als site-overschrijdende scripts.
