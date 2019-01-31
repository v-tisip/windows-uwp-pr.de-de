---
<<<<<<< HEAD "author": Karl-Bridge-Microsoft-Beschreibung: Optimieren Sie Ihre app für die Eingabe von Xbox-Gamepad und Fernbedienung zu erhalten.
=== Beschreibung: TODO
>>>>>>> Master / Titel: Gamepad und Fernbedienung Interaktionen ms.assetid: 784a08dc-2736-4bd3-bea0-08da16b1bd47 Bezeichnung: Gamepad und remote Interaktionen Vorlage: detail.hbs IsNew: "true" <<<<<<< HEAD ms.author: Kbridge =======
master MS.Date: 02/08/2017 ms.topic: Artikel Schlüsselwörter: Windows 10, Uwp ms.localizationpriority: Mittel
---
# <a name="gamepad-and-remote-control-interactions"></a>Interaktionen von Gamepad und Fernbedienung

![Bild von Tastatur und Gamepad](images/keyboard/keyboard-gamepad.jpg)

***Allgemeine Interaktionsmuster sind zwischen Tastatur, Gamepad und Fernbedienung gleich.***

Der wichtigste Schritt bei der Optimierung für 10-Fuß-Umgebungen besteht darin, sicherzustellen, dass Ihre App gut mit Gamepads und Fernbedienungen funktioniert. Es gibt spezifische Verbesserungen für Gamepads und Fernbedienungen, mit denen Sie die Interaktionserfahrungen von Benutzern auf Geräten optimieren können, auf denen ihre Aktionen eher eingeschränkt sind.

Universelle Windows-Plattform (UWP)-Apps unterstützen jetzt die Eingabe per Gamepad und Fernbedienung. 

Gamepads und Remotesteuerungen sind die primären Eingabegeräte in Xbox- und TV-Umgebungen. 

UWP-Apps sollten für diese Eingabegerätetypen ebenso optimiert werden wie für die Eingabe per Tastatur und Maus auf einem PC oder für die Toucheingabe auf einem Smartphone oder Tablet. 

Der wichtigste Schritt bei der Optimierung für Xbox und Fernseher besteht darin, sicherzustellen, dass die App gut mit diesen Eingabegeräten funktioniert.

Es ist jetzt möglich, das Gamepad an einen PC anzuschließen und mit UWP-Apps zu verwenden. Die Überprüfung Ihrer Arbeit wird somit erleichtert.

Um bei Verwendung eines Gamepads oder einer Fernbedienung eine funktionierende und praktische Benutzeroberfläche für Ihre UWP-App zu gewährleisten, sollten Sie Folgendes beachten:

* [Hardwaretasten](../devices/designing-for-tv.md#hardware-buttons): Die Tasten und Konfigurationen von Gamepad und Fernbedienung unterscheiden sich stark.

* [XY-Fokusnavigation und Interaktion](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction): Mithilfe der XY-Fokusnavigation können die Benutzer auf der Benutzeroberfläche Ihrer App navigieren.

* [Mausmodus](../devices/designing-for-tv.md#mouse-mode): Im Mausmodus kann Ihre App eine Mauseingabe emulieren, wenn die XY Fokusnavigation nicht ausreichend ist.
