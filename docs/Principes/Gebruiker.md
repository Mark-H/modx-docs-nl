# Gebruiker

Gebruikers in MODX kunnen veel verschillende toegangsniveaus hebben afhankelijk van de gebruikersgroepen waar ze toegang tot hebben.

In MODX Revolution (2.x) is er dan ook geen verschil tussen een frontend en backend gebruiker zoals er in MODX Evolution (1.x) wel was. In Revolution bepaal je met toegangsniveaus of een gebruiker toegang tot de manager of frontend heeft.

## Gebruikers Waarden
MODX kent voor gebruikers de volgende velden. Technisch gezien bestaat een gebruiker uit 2 dingen: een Gebruiker (modUser class) en een Profiel (modUserProfile class). Wanneer je met custom code deze velden wilt benaderen is het dus van belang het juiste object te laden.

| Veldnaam | Class | Omschrijving|
|--|--|--|
| id | beide | Bij modUser is dit het Gebruikers ID,  bij modUserProfile is dit het ID van het modUserProfile record. 9 van de 10 keer zijn deze hetzelfde, maar er kunnen situaties optreden waarbij dit *niet* het geval is, dus hou hier rekening mee bij het programmeren waar gebruikers in voor komen.
| internalKey | modUserProfile | Het relationeel ID van het profiel naar de gebruiker toe.
| username | modUser | De gebruikersnaam van een gebruiker. Is uniek.
| password | modUser | Het gehashte wachtwoord van de gebruiker. Sinds 2.1 wordt er standaard gebruik gemaakt van PDFKB2 en een unieke gebruikershash, welke een zeer veilige en moeilijk te kraken hash oplevert. Let wel: bij een upgrade van 2.0.x naar 2.1 of 2.2 worden NIET automatisch wachtwoorden herschreven van md5 (gebruikte hash in Evolution (1.x) en Revolution 2.0.x) naar PDFKB2 - installeer hiervoor de PDFKB2 plugin welke bij het inloggen het wachtwoord opnieuw hasht en opslaat.
| hash_class | modUser | De class die gebruikt is om het wachtwoord te hashen. Dit kan modMD5 zijn (standaard voor Evolution en 2.0.x) of sinds 2.1 modPDFKB2. 
| salt | modUser | Unieke salt waarmee het wachtwoord van de gebruiker gehasht is.
| email | modUserProfile | Het e-mailadres van de gebruiker. Hoeft niet per se uniek te zijn afhankelijk van systeem instellingen.
| fullname | modUserProfile | De naam van de gebruiker.
| dob | modUserProfile | De geboortedatum van de gebruiker.
| extended | modUserProfile | Een speciaal veld waarin een array van custom velden worden opgeslagen. Kan gebruikt worden om extra gebruiker data in op te slaan. 
| remote_key | modUserProfile | Dit veld is niet beschikbaar in de interface, maar kan worden gebruikt door snippets/plugins om een gebruiker een extern referentienummer mee te geven, bijvoorbeeld bij SSO met een extern login systeem.

** !! Incompleet **