---
<span data-ttu-id="04708-101"><<<<<<< HEAD "author": Karl-Bridge-Microsoft-Beschreibung: Optimieren Sie Ihre app für die Eingabe von Xbox-Gamepad und Fernbedienung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="04708-101"><<<<<<< HEAD author: Karl-Bridge-Microsoft Description: Optimize your app for input from Xbox gamepad and remote control.</span></span>
<span data-ttu-id="04708-102">=== Beschreibung: TODO</span><span class="sxs-lookup"><span data-stu-id="04708-102">======= Description: TODO</span></span>
>>>>>>> <span data-ttu-id="04708-103">Master / Titel: Gamepad und Fernbedienung Interaktionen ms.assetid: 784a08dc-2736-4bd3-bea0-08da16b1bd47 Bezeichnung: Gamepad und remote Interaktionen Vorlage: detail.hbs IsNew: "true" <<<<<<< HEAD ms.author: Kbridge =======
master MS.Date: 02/08/2017 ms.topic: Artikel Schlüsselwörter: Windows 10, Uwp ms.localizationpriority: Mittel</span><span class="sxs-lookup"><span data-stu-id="04708-103">master title: Gamepad and remote control interactions ms.assetid: 784a08dc-2736-4bd3-bea0-08da16b1bd47 label: Gamepad and remote interactions template: detail.hbs isNew: true <<<<<<< HEAD ms.author: kbridge =======
master ms.date: 02/08/2017 ms.topic: article keywords: windows 10, uwp ms.localizationpriority: medium</span></span>
---
# <a name="gamepad-and-remote-control-interactions"></a><span data-ttu-id="04708-104">Interaktionen von Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="04708-104">Gamepad and remote control interactions</span></span>

![Bild von Tastatur und Gamepad](images/keyboard/keyboard-gamepad.jpg)

***<span data-ttu-id="04708-106">Allgemeine Interaktionsmuster sind zwischen Tastatur, Gamepad und Fernbedienung gleich.</span><span class="sxs-lookup"><span data-stu-id="04708-106">Common interaction patterns are shared between gamepad, remote control, and keyboard</span></span>***

<span data-ttu-id="04708-107">Der wichtigste Schritt bei der Optimierung für 10-Fuß-Umgebungen besteht darin, sicherzustellen, dass Ihre App gut mit Gamepads und Fernbedienungen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="04708-107">Making sure that your app works well with gamepad and remote is the most important step in optimizing for 10-foot experiences.</span></span> <span data-ttu-id="04708-108">Es gibt spezifische Verbesserungen für Gamepads und Fernbedienungen, mit denen Sie die Interaktionserfahrungen von Benutzern auf Geräten optimieren können, auf denen ihre Aktionen eher eingeschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="04708-108">There are several gamepad and remote-specific improvements that you can make to optimize the user interaction experience on a device where their actions are somewhat limited.</span></span>

<span data-ttu-id="04708-109">Universelle Windows-Plattform (UWP)-Apps unterstützen jetzt die Eingabe per Gamepad und Fernbedienung.</span><span class="sxs-lookup"><span data-stu-id="04708-109">Universal Windows Platform (UWP) apps now support gamepad and remote control input.</span></span> 

<span data-ttu-id="04708-110">Gamepads und Remotesteuerungen sind die primären Eingabegeräte in Xbox- und TV-Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="04708-110">Gamepads and remote controls are the primary input devices for Xbox and TV experiences.</span></span> 

<span data-ttu-id="04708-111">UWP-Apps sollten für diese Eingabegerätetypen ebenso optimiert werden wie für die Eingabe per Tastatur und Maus auf einem PC oder für die Toucheingabe auf einem Smartphone oder Tablet.</span><span class="sxs-lookup"><span data-stu-id="04708-111">UWP apps should be optimized for these input device types, just like they are for keyboard and mouse input on a PC, and touch input on a phone or tablet.</span></span> 

<span data-ttu-id="04708-112">Der wichtigste Schritt bei der Optimierung für Xbox und Fernseher besteht darin, sicherzustellen, dass die App gut mit diesen Eingabegeräten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="04708-112">Making sure that your app works well with these input devices is the most important step when optimizing for Xbox and the TV.</span></span>

<span data-ttu-id="04708-113">Es ist jetzt möglich, das Gamepad an einen PC anzuschließen und mit UWP-Apps zu verwenden. Die Überprüfung Ihrer Arbeit wird somit erleichtert.</span><span class="sxs-lookup"><span data-stu-id="04708-113">You can now plug in and use the gamepad with UWP apps on PC which makes validating the work easy.</span></span>

<span data-ttu-id="04708-114">Um bei Verwendung eines Gamepads oder einer Fernbedienung eine funktionierende und praktische Benutzeroberfläche für Ihre UWP-App zu gewährleisten, sollten Sie Folgendes beachten:</span><span class="sxs-lookup"><span data-stu-id="04708-114">To ensure a successful and enjoyable user experience for your UWP app when using a gamepad or remote control, you should consider the following:</span></span>

* <span data-ttu-id="04708-115">[Hardwaretasten](../devices/designing-for-tv.md#hardware-buttons): Die Tasten und Konfigurationen von Gamepad und Fernbedienung unterscheiden sich stark.</span><span class="sxs-lookup"><span data-stu-id="04708-115">[Hardware buttons](../devices/designing-for-tv.md#hardware-buttons) - The gamepad and remote provide very different buttons and configurations.</span></span>

* <span data-ttu-id="04708-116">[XY-Fokusnavigation und Interaktion](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction): Mithilfe der XY-Fokusnavigation können die Benutzer auf der Benutzeroberfläche Ihrer App navigieren.</span><span class="sxs-lookup"><span data-stu-id="04708-116">[XY focus navigation and interaction](../devices/designing-for-tv.md#xy-focus-navigation-and-interaction) - XY focus navigation enables the user to navigate around your app's UI.</span></span>

* <span data-ttu-id="04708-117">[Mausmodus](../devices/designing-for-tv.md#mouse-mode): Im Mausmodus kann Ihre App eine Mauseingabe emulieren, wenn die XY Fokusnavigation nicht ausreichend ist.</span><span class="sxs-lookup"><span data-stu-id="04708-117">[Mouse mode](../devices/designing-for-tv.md#mouse-mode) - Mouse mode lets your app emulate a mouse experience when XY focus navigation isn't sufficient.</span></span>
