- INSTALLATIE

<pre>

1. Installeer Java op uw desktop, Java 1.7 t/m Java 1.16 wordt in deze versie ondersteund.

2. Installeer de nieuwste versie van OpenAS2 hier: https://sourceforge.net/projects/openas2/files (Deze configuratie is gemaakt op v3.5.0)

3. Installeer JCE Policy bestanden hier: http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html (maak eenmalig een account aan indien nodig)

4. Maak een backup voordat u met deze stap verder gaat; verplaats de JCE bestanden in uw Java/lib/security folder. (local_policy.jar & US_export_policy.jar)

5. Haal de bestanden uit de OpenAS2 folder en plaats ze in een makkelijk te bereiken folder, bijvoorbeeld Downloads.

- Grotere bestanden kosten meer geheugen, allocate t/m 4GB RAM toe aan OpenAS2 bij bestanden tot 750MB. In 'start_openas2.bat/.sh', zoek naar '-Xmx' en verander hier het nummer van 384m naar hoeveel nodig is.

6. Navigeer naar uw OpenAS2 folder. Om de server te starten, run bin/start-openas2.bat/.sh (zorg ervoor dat scripts executable zijn op Linux)

</pre>

- CONFIGURATIE

<pre>

1. Navigeer naar uw OpenAS2 folder. Configureer uw verstuurgegevens in config/partnerships.xml vanaf regel 3.

Hierbij is belangrijk dat u de correcte gegevens van uzelf en van de andere partij correct noteert. Indien er meer dan 1 ontvanger is; maak nog een partnership aan.

2. Configureer de bericht-versturende server door uw eigen publieke IP-adres te noteren. Laat de port (:10080/1) hetzelfde.

3. Configureer uw ontvangstgegevens in config/config.xml vanaf regel 3.

4. Configureer de bericht-ontvangende server door uw eigen publieke IP-adres te noteren. Laat de port (:10080/1) hetzelfde.

</pre>

- CERTIFICATIE EN KEYSTORES

<pre>

1. Installeer een keystore beheerder zoals: http://keystore-explorer.org/downloads.html

2. Open uw OpenAS2 folder. Navigeer naar config/as2_certs.p12 en open dit bestand. Indien er geen wachtwoord verkrijgbaar is, ga naar stap 4.

3. De default keystores in dit bestand zijn 'openas2a' en 'openas2b'. Maak een nieuwe Key Pair aan met de volgende gegevens:
Algoritme: RSA (Key Size 2.048), Signatuur: SHA-256 met RSA, Validity: eigen voorkeur, Name: passende naam bij uw verzender/ontvanger.

4. Open Keystore Explorer en maak een nieuwe Key Store aan. Klik op New Key Pair en voeg de volgende gegevens toe:
Algoritme: RSA (Key Size 2.048), Signatuur: SHA-256 met RSA, Validity: eigen voorkeur, Name: passende naam bij uw verzender/ontvanger.

Hierna zal gevraagd worden om een wachtwoord, noteer dit; het is nodig voor de volgende stappen.

5. Klik op de zojuist aangemaakte Key Store. Klik op de optie 'Export' en selecteer 'Export Certificate Chain'.

Hierbij is de OpenAS2 configuratie afgerond.

</pre>

- AS2GATEWAY

<pre>

1. Maak een account aan op AS2Gateway: https://console.as2gateway.com/login

2. Log in op uw account. Aan de linkerkant is een taakbalk met meerdere icons. Selecteer 'Stations'.

3. Klik op de knop 'New Station' bovenaan het scherm en configureer uw eigen gegevens die u eerder hebt aangemaakt in partnerships.xml; gebruik uit het deze repo het voorbeeld 'company-y'. (in het voorbeeld van deze repo dus 'company-y-as2-id')

4. De rest van de configuratie is best vanzelfsprekend, sla het Station op en navigeer naar de taakbalk icon 'Partners'. Maak hier ook een nieuwe partner aan, met de gegevens uit config.xml; gebruik uit de repo het voorbeeld 'company-x'

5. In de Partner configuratie, gebruik uw eigen IP-adres als ontvanger zoals ingesteld in config.xml:66 (http://my-public-ip:10081)

6. Upload uw zelf-gemaakte encryptie folder uit stap 5 van 'CERTIFICATIE EN KEYSTORES' onderin de Partner configuratie en sla het op.

7. Om berichten te sturen, navigeer naar OpenAS2/bin/start-openas2.bat/.sh en run het bestand. Ga terug naar het AS2Gateway dashboard en klik op 'New message' in de taakbalk.

</pre>

Bij eventuele problemen, open een issue in deze repository.