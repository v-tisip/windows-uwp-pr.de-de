---
author: Mtoepke
title: Bekannte Probleme mit UWP im Zusammenhang mit dem Xbox One-Entwicklerprogramm
description: Beschreibt die bekannten Probleme für UWP im Xbox Developer-Programm.
ms.author: mstahl
ms.date: 03/29/2017
ms.topic: article
keywords: windows10, UWP
ms.assetid: a7b82570-1f99-4bc3-ac78-412f6360e936
ms.localizationpriority: medium
ms.openlocfilehash: 798192dd898af5a7107087b4a9708e1a1d0cb9b5
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7286509"
---
# <a name="known-issues-with-uwp-on-xbox-developer-program"></a><span data-ttu-id="e6aea-104">Bekannte Probleme mit UWP im Zusammenhang mit dem Xbox One-Entwicklerprogramm</span><span class="sxs-lookup"><span data-stu-id="e6aea-104">Known issues with UWP on Xbox Developer Program</span></span>

<span data-ttu-id="e6aea-105">Dieses Thema beschreibt bekannte Probleme im Zusammenhang mit dem Xbox One-Entwicklerprogramm.</span><span class="sxs-lookup"><span data-stu-id="e6aea-105">This topic describes known issues with the UWP on Xbox One Developer Program.</span></span> <span data-ttu-id="e6aea-106">Weitere Informationen zu diesem Programm finden Sie unter [UWP auf Xbox](index.md).</span><span class="sxs-lookup"><span data-stu-id="e6aea-106">For more information about this program, see [UWP on Xbox](index.md).</span></span> 

<span data-ttu-id="e6aea-107">\[Wenn Sie über einen Link in einem API-Referenzthema hierher gelangten und nach Informationen zu APIs für die Universal-Gerätefamilie suchen, lesen Sie bitte [UWP-Funktionen, die noch nicht auf Xbox One unterstützt werden](http://go.microsoft.com/fwlink/?LinkID=760755).\]</span><span class="sxs-lookup"><span data-stu-id="e6aea-107">\[If you came here from a link in an API reference topic, and are looking for Universal device family API information, please see [UWP features that aren't yet supported on Xbox](http://go.microsoft.com/fwlink/?LinkID=760755).\]</span></span>

<span data-ttu-id="e6aea-108">In der folgenden Liste werden einige bekannte Probleme aufgelistet, die auftreten können. Diese Liste ist jedoch nicht vollständig.</span><span class="sxs-lookup"><span data-stu-id="e6aea-108">The following list highlights some known issues that you may encounter, but this list is not exhaustive.</span></span> 

<span data-ttu-id="e6aea-109">**Wir möchten gerne Ihr Feedback erhalten.** Melden Sie daher alle festgestellten Probleme im Forum für das [Entwickeln von Apps für die Universelle Windows-Plattform (UWP)](https://social.msdn.microsoft.com/forums/windowsapps/home?forum=wpdevelop).</span><span class="sxs-lookup"><span data-stu-id="e6aea-109">**We want to get your feedback**, so please report any issues that you find on the [Developing Universal Windows Platform apps](https://social.msdn.microsoft.com/forums/windowsapps/home?forum=wpdevelop) forum.</span></span> 

<span data-ttu-id="e6aea-110">Wenn Sie Probleme haben, lesen Sie die Informationen in diesem Thema, informieren Sie sich in den [häufig gestellten Fragen](frequently-asked-questions.md), und nutzen Sie die Foren, um Hilfe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e6aea-110">If you get stuck, read the information in this topic, see [Frequently asked questions](frequently-asked-questions.md), and use the forums to ask for help.</span></span>

 
## <a name="deploying-from-vs-fails-with-parental-controls-turned-on"></a><span data-ttu-id="e6aea-111">Fehler bei der Bereitstellung aus VS bei aktiviertem Jugendschutz</span><span class="sxs-lookup"><span data-stu-id="e6aea-111">Deploying from VS fails with Parental Controls turned on</span></span>

<span data-ttu-id="e6aea-112">Beim Starten Ihrer App in VS tritt ein Fehler auf, wenn in den Einstellungen der Konsole der Jugendschutz aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="e6aea-112">Launching your app from VS will fail if the console has Parental Controls turned on in Settings.</span></span>

<span data-ttu-id="e6aea-113">Um dieses Problem zu umgehen, deaktivieren Sie vorübergehend den Jugendschutz. Alternative:</span><span class="sxs-lookup"><span data-stu-id="e6aea-113">To work around this issue, either temporarily disable Parental Controls, or:</span></span>
1. <span data-ttu-id="e6aea-114">Stellen Sie Ihre App in der Konsole mit deaktiviertem Jugendschutz bereit.</span><span class="sxs-lookup"><span data-stu-id="e6aea-114">Deploy your app to the console with Parental Controls turned off.</span></span>
2. <span data-ttu-id="e6aea-115">Aktivieren Sie den Jugendschutz.</span><span class="sxs-lookup"><span data-stu-id="e6aea-115">Turn on Parental Controls.</span></span>
3. <span data-ttu-id="e6aea-116">Starten Sie die App von der Konsole.</span><span class="sxs-lookup"><span data-stu-id="e6aea-116">Launch your app from the console.</span></span>
4. <span data-ttu-id="e6aea-117">Geben Sie eine PIN oder ein Kennwort ein, um das Starten der App zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="e6aea-117">Enter a PIN or password to allow the app to launch.</span></span>
5. <span data-ttu-id="e6aea-118">Die App wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="e6aea-118">App will launch.</span></span>
6. <span data-ttu-id="e6aea-119">Schließen Sie die App.</span><span class="sxs-lookup"><span data-stu-id="e6aea-119">Close the app.</span></span>
7. <span data-ttu-id="e6aea-120">Starten Sie die App in VS mithilfe von F5. Sie wird ohne Benutzeraufforderung gestartet.</span><span class="sxs-lookup"><span data-stu-id="e6aea-120">Launch from VS using F5, and the app will launch with no prompting.</span></span>

<span data-ttu-id="e6aea-121">Zu diesem Zeitpunkt bleibt die Berechtigung so lange _bestehen_, bis Sie den Benutzer abmelden, auch wenn Sie die App deinstallieren und neu installieren.</span><span class="sxs-lookup"><span data-stu-id="e6aea-121">At this point the permission is _sticky_ until you sign the user out, even if you uninstall and reinstall the app.</span></span>
 
<span data-ttu-id="e6aea-122">Es gibt eine weitere Ausnahme, die nur für Kinderkonten verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e6aea-122">There is another type of exemption that is only available for child accounts.</span></span> <span data-ttu-id="e6aea-123">Bei einem Kinderkonto muss sich ein Elternteil anmelden, um die Berechtigung zu erteilen. In diesem Fall kann der Elternteil die Option **Immer** auswählen, um dem Kind das Starten der App zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="e6aea-123">A child account requires a parent to sign in to grant permission, but when they do, the parent has the option of choosing to **Always** allow the child to launch the app.</span></span> <span data-ttu-id="e6aea-124">Diese Ausnahme wird in der Cloud gespeichert und bleibt bestehen, auch wenn sich das Kind abmeldet und wieder anmeldet.</span><span class="sxs-lookup"><span data-stu-id="e6aea-124">That exemption is stored in the cloud and will persist even if the child signs out and signs back in.</span></span>

## <a name="storagefilecopyasync-fails-to-copy-encrypted-files-to-unencrypted-destination"></a><span data-ttu-id="e6aea-125">StorageFile.CopyAsync kopiert verschlüsselte Dateien nicht an ein unverschlüsseltes Ziel.</span><span class="sxs-lookup"><span data-stu-id="e6aea-125">StorageFile.CopyAsync fails to copy encrypted files to unencrypted destination</span></span> 

<span data-ttu-id="e6aea-126">Wenn StorageFile.CopyAsync verwendet wird, um eine verschlüsselte Datei an ein Ziel zu kopieren, das nicht verschlüsselt ist, schlägt der Aufruf mit folgender Ausnahme fehl:</span><span class="sxs-lookup"><span data-stu-id="e6aea-126">When StorageFile.CopyAsync is used to copy a file that is encrypted to a destination that is not encrypted, the call will fail with the following exception:</span></span>

```
System.UnauthorizedAccessException: Access is denied. (Excep_FromHResult 0x80070005)
```

<span data-ttu-id="e6aea-127">Dies kann sich auf Xbox-Entwickler auswirken, die Dateien kopieren möchten, die als Teil ihres App-Pakets an einem anderen Speicherort bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e6aea-127">This can affect Xbox developers who want to copy files that are deployed as part of their app package to another location.</span></span> <span data-ttu-id="e6aea-128">Der Grund hierfür ist, dass der Inhalt des Pakets auf einer Xbox im Einzelhandelsmodus verschlüsselt ist, aber im Entwicklermodus nicht.</span><span class="sxs-lookup"><span data-stu-id="e6aea-128">The reason for this is that the package contents are encrypted on an Xbox in retail mode, but not in Dev Mode.</span></span> <span data-ttu-id="e6aea-129">Daher kann die App während der Entwicklungs- und Testphase scheinbar wie erwartet funktionieren, aber dann Fehler aufweisen, sobald sie veröffentlicht und auf einer Einzelhandels-Xbox installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="e6aea-129">As a result, the app may appear to work as expected during development and testing, but then fail once it has been published and then installed to a retail Xbox.</span></span>
 

## <a name="blocked-networking-ports-on-xbox-one"></a><span data-ttu-id="e6aea-130">Gesperrte Netzwerkports auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="e6aea-130">Blocked networking ports on Xbox One</span></span>

<span data-ttu-id="e6aea-131">Bindungen an Ports im Bereich [57344, 65535] (einschließlich) sind für Apps für die universelle Windows-Plattform (UWP) auf Xbox One-Geräten nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="e6aea-131">Universal Windows Platform (UWP) apps on Xbox One devices are restricted from binding to ports in the range [57344, 65535], inclusive.</span></span> <span data-ttu-id="e6aea-132">Obwohl die Bindung an diese Ports während der Laufzeit erfolgreich zu sein scheint, kann Netzwerkdatenverkehr im Hintergrund gelöscht werden, bevor er Ihre App erreicht.</span><span class="sxs-lookup"><span data-stu-id="e6aea-132">Although binding to these ports might appear to succeed at run-time, network traffic can be silently dropped before reaching your app.</span></span> <span data-ttu-id="e6aea-133">Ihre App sollte an den Port0 gebunden werden, wann immer möglich. Dieser ermöglicht dem System die Auswahl des lokalen Ports.</span><span class="sxs-lookup"><span data-stu-id="e6aea-133">Your app should bind to port 0 wherever possible, which allows the system to select the local port.</span></span> <span data-ttu-id="e6aea-134">Wenn Sie einen bestimmten Port verwenden müssen, muss sich die Portnummer im Bereich [1025, 49151] befinden, und Sie sollten Konflikte mit der IANA-Registrierung überprüfen und vermeiden.</span><span class="sxs-lookup"><span data-stu-id="e6aea-134">If you need to use a specific port, the port number must be in the range [1025, 49151], and you should check and avoid conflicts with the IANA registry.</span></span> <span data-ttu-id="e6aea-135">Weitere Informationen finden Sie in [Dienstname und Transportprotokoll-Portnummer-Registrierung](http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).</span><span class="sxs-lookup"><span data-stu-id="e6aea-135">For more information, see the [Service Name and Transport Protocol Port Number Registry](http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).</span></span>

## <a name="uwp-api-coverage"></a><span data-ttu-id="e6aea-136">UWP-API-Abdeckung</span><span class="sxs-lookup"><span data-stu-id="e6aea-136">UWP API coverage</span></span>

<span data-ttu-id="e6aea-137">Nicht alle UWP-APIs werden auf Xbox unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e6aea-137">Not all UWP APIs are supported on Xbox.</span></span> <span data-ttu-id="e6aea-138">Die Liste der APIs, von denen bekannt ist, dass sie nicht funktionieren, finden Sie in [UWP-Funktionen, die noch nicht auf Xbox One unterstützt werden](http://go.microsoft.com/fwlink/p/?LinkId=760755).</span><span class="sxs-lookup"><span data-stu-id="e6aea-138">For the list of APIs that we know don’t work, see [UWP features that aren't yet supported on Xbox](http://go.microsoft.com/fwlink/p/?LinkId=760755).</span></span> <span data-ttu-id="e6aea-139">Wenn Sie Probleme mit anderen APIs feststellen, melden Sie dies bitte in den Foren.</span><span class="sxs-lookup"><span data-stu-id="e6aea-139">If you find issues with other APIs, please report them on the forums.</span></span> 


## <a name="navigating-to-wdp-causes-a-certificate-warning"></a><span data-ttu-id="e6aea-140">Navigieren zu WDP führt zu einer Zertifikatwarnung</span><span class="sxs-lookup"><span data-stu-id="e6aea-140">Navigating to WDP causes a certificate warning</span></span>

<span data-ttu-id="e6aea-141">Sie erhalten eine Warnung zum Zertifikat, das bereitgestellt wurde, ähnlich wie folgender Screenshot, dass das von Ihrer Xbox One-Konsole signierte Sicherheitszertifikat nicht als bekannter vertrauenswürdiger Herausgeber betrachtet wird.</span><span class="sxs-lookup"><span data-stu-id="e6aea-141">You will receive a warning about the certificate that was provided, similar to the following screenshot, because the security certificate signed by your Xbox One console is not considered a well-known trusted publisher.</span></span> <span data-ttu-id="e6aea-142">Klicken Sie auf **Laden dieser Website fortsetzen**, um auf das Windows Device Portal zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="e6aea-142">To access the Windows Device Portal, click **Continue to this website**.</span></span>

![Warnung zum Sicherheitszertifikat der Website](images/security_cert_warning.jpg)


## <a name="knownfoldersmediaserverdevices-caveat-on-xbox"></a><span data-ttu-id="e6aea-144">KnownFolders.MediaServerDevices Einschränkung auf Xbox</span><span class="sxs-lookup"><span data-stu-id="e6aea-144">KnownFolders.MediaServerDevices caveat on Xbox</span></span>

<span data-ttu-id="e6aea-145">Auf dem Desktop sind Medienserver mit dem PC „gekoppelt“, und der Gerätezuordnungsdienst (Device Association Service) verfolgt ständig, welcher der Server aktuell online ist. Mit einer Erstabfrage des Dateisystems kann sofort eine Liste der verbundenen Server zurückgegeben werden, die derzeit online sind.</span><span class="sxs-lookup"><span data-stu-id="e6aea-145">On Desktop, media servers are “paired” with the PC, and the Device Association Service is constantly tracking which of the servers are currently on-line, so an initial file system query can immediately return a list of the paired servers that are currently online.</span></span>

<span data-ttu-id="e6aea-146">Auf der Xbox gibt es keine UI, um Server hinzuzufügen oder zu löschen. Deshalb wird die Erstabfrage auf das Dateisystem immer leer sein.</span><span class="sxs-lookup"><span data-stu-id="e6aea-146">On Xbox, there is no UI to add or remove servers, so the initial file system query will always return empty.</span></span> <span data-ttu-id="e6aea-147">Sie müssen eine Abfrage erstellen, das ContentsChanged-Ereignis abonnieren, und die Abfrage bei jeder Benachrichtigung aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e6aea-147">You must create a query and subscribe to the ContentsChanged event and refresh the query each time you get a notification.</span></span> <span data-ttu-id="e6aea-148">Die Server werden durchgelassen, und die meisten innerhalb von drei Sekunden erkannt.</span><span class="sxs-lookup"><span data-stu-id="e6aea-148">Servers will trickle in and most will have been discovered within 3 seconds.</span></span>

<span data-ttu-id="e6aea-149">Einfacher Beispielcode:</span><span class="sxs-lookup"><span data-stu-id="e6aea-149">Simple example code:</span></span>

```
namespace TestDNLA {

    public sealed partial class MainPage : Page {
        public MainPage() {
            this.InitializeComponent();
        }

        private async void FindFiles_Click(object sender, RoutedEventArgs e) {
            try {
                StorageFolder library = KnownFolders.MediaServerDevices;
                var folderQuery = library.CreateFolderQuery();
                folderQuery.ContentsChanged += FolderQuery_ContentsChanged;
                IReadOnlyList<StorageFolder> rootFolders = await folderQuery.GetFoldersAsync();
                if (rootFolders.Count == 0) {
                    Debug.WriteLine("No Folders found");
                } else {
                    Debug.WriteLine("Folders found");
                }
            } catch (Exception ex) {
                Debug.WriteLine("Error: " + ex.Message);
            } finally {
                Debug.WriteLine("Done");
            }
        }

        private async void FolderQuery_ContentsChanged(Windows.Storage.Search.IStorageQueryResultBase sender, object args) {
            Debug.WriteLine("Folder added " + sender.Folder.Name);
            IReadOnlyList<StorageFolder> topLevelFolders = await sender.Folder.GetFoldersAsync();
            foreach (StorageFolder topLevelFolder in topLevelFolders) {
                Debug.WriteLine(topLevelFolder.Name);
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e6aea-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e6aea-150">See also</span></span>
- [<span data-ttu-id="e6aea-151">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="e6aea-151">Frequently asked questions</span></span>](frequently-asked-questions.md)
- [<span data-ttu-id="e6aea-152">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="e6aea-152">UWP on Xbox One</span></span>](index.md)
