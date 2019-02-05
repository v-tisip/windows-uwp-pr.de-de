---
Description: Use speech recognition to provide input, specify an action or command, and accomplish tasks.
title: Spracherkennung
ms.assetid: 553C0FB7-35BC-4894-9EF1-906139E17552
label: Speech recognition
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 1b7eec51044a70b0738e246d3aa516c37643cf68
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9048547"
---
# <a name="speech-recognition"></a><span data-ttu-id="50acf-103">Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="50acf-103">Speech recognition</span></span>


<span data-ttu-id="50acf-104">Nutzen Sie die Spracherkennung als Eingabemöglichkeit oder zum Ausführen einer Aktion, eines Befehls oder einer Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="50acf-104">Use speech recognition to provide input, specify an action or command, and accomplish tasks.</span></span>

> <span data-ttu-id="50acf-105">**Wichtige APIs**: [**Windows.Media.SpeechRecognition**](https://msdn.microsoft.com/library/windows/apps/dn653262)</span><span class="sxs-lookup"><span data-stu-id="50acf-105">**Important APIs**: [**Windows.Media.SpeechRecognition**](https://msdn.microsoft.com/library/windows/apps/dn653262)</span></span>

<span data-ttu-id="50acf-106">Die Spracherkennung besteht aus einer Sprachlaufzeit, Erkennungs-APIs zum Programmieren der Laufzeit, einsatzfähiger Grammatik für das Diktieren und die Websuche und einer Standard-UI, die Benutzern das Auffinden und Verwenden der Spracherkennungsfeatures erleichtert.</span><span class="sxs-lookup"><span data-stu-id="50acf-106">Speech recognition is made up of a speech runtime, recognition APIs for programming the runtime, ready-to-use grammars for dictation and web search, and a default system UI that helps users discover and use speech recognition features.</span></span>

## <a name="configure-speech-recognition"></a><span data-ttu-id="50acf-107">Konfigurieren Sie die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="50acf-107">Configure speech recognition</span></span>

<span data-ttu-id="50acf-108">Um die Spracherkennung mit Ihrer app zu unterstützen, muss der Benutzer verbinden und ein Mikrofon auf ihrem Gerät aktivieren, und akzeptieren Sie die Microsoft-Datenschutzrichtlinie Berechtigung für Ihre app um sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="50acf-108">To support speech recognition with your app, the user must connect and enable a microphone on their device, and accept the Microsoft Privacy Policy granting permission for your app to use it.</span></span>

<span data-ttu-id="50acf-109">Den Benutzer automatisch aufgefordert, mit der ein systemdialogfeld anfordern und Zugriffsberechtigung für das Mikrofon verwenden des Audio feed nur Satz (beispielsweise von der [Spracherkennung Beispiel und Sprachsynthese](https://go.microsoft.com/fwlink/p/?LinkID=619897) unten dargestellt) das **Mikrofon** [Gerät Funktion](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-devicecapability) in der [App-Paket-manifest](https://docs.microsoft.com/uwp/schemas/appxpackage/appx-package-manifest).</span><span class="sxs-lookup"><span data-stu-id="50acf-109">To automatically prompt the user with a system dialog requesting permission to access and use the microphone's audio feed (example from the [Speech recognition and speech synthesis sample](https://go.microsoft.com/fwlink/p/?LinkID=619897) shown below), just set the **Microphone** [device capability](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-devicecapability) in the [App package manifest](https://docs.microsoft.com/uwp/schemas/appxpackage/appx-package-manifest).</span></span> <span data-ttu-id="50acf-110">Weitere Details finden Sie in der [Deklaration der App](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span><span class="sxs-lookup"><span data-stu-id="50acf-110">For more detail, see [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span></span>

![Datenschutzrichtlinie für den Zugriff auf das Mikrofon](images/speech/privacy.png)

<span data-ttu-id="50acf-112">Klickt der Benutzer auf "Ja", um Zugriff auf das Mikrofon gewähren, wird Ihre app zur Liste der zugelassenen Anwendungen auf die Einstellungen hinzugefügt-> Datenschutz-> Mikrofon Seite.</span><span class="sxs-lookup"><span data-stu-id="50acf-112">If the user clicks Yes to grant access to the microphone, your app is added to the list of approved applications on the Settings -> Privacy -> Microphone page.</span></span> <span data-ttu-id="50acf-113">Jedoch, wie der Benutzer auswählen kann, um diese Einstellung zu einem beliebigen Zeitpunkt zu deaktivieren, sollten Sie sicherstellen, dass Ihre app Zugriff auf das Mikrofon hat, bevor Sie versuchen, es zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="50acf-113">However, as the user can choose to turn this setting off at any time, you should confirm that your app has access to the microphone before attempting to use it.</span></span>

<span data-ttu-id="50acf-114">Wenn Sie auch diktieren, Cortana, unterstützen möchten, oder andere Spracherkennung-(z. B. eine [vordefinierte Grammatik](#predefined-grammars) in eine Einschränkung zu einem Thema definiert Dienste), Sie müssen sich vergewissern, dass **Online-Spracherkennung** (Einstellungen-> Datenschutz-> Sprache) ist aktiviert.</span><span class="sxs-lookup"><span data-stu-id="50acf-114">If you also want to support dictation, Cortana, or other speech recognition services (such as a [predefined grammar](#predefined-grammars) defined in a topic constraint), you must also confirm that **Online speech recognition** (Settings -> Privacy -> Speech) is enabled.</span></span>

<span data-ttu-id="50acf-115">Dieser Codeausschnitt zeigt, wie Ihre app überprüfen kann, wenn ein Mikrofon vorhanden ist und sie berechtigt sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="50acf-115">This snippet shows how your app can check if a microphone is present and if it has permission to use it.</span></span>

```csharp
public class AudioCapturePermissions
{
    // If no microphone is present, an exception is thrown with the following HResult value.
    private static int NoCaptureDevicesHResult = -1072845856;

    /// <summary>
    /// Note that this method only checks the Settings->Privacy->Microphone setting, it does not handle
    /// the Cortana/Dictation privacy check.
    ///
    /// You should perform this check every time the app gets focus, in case the user has changed
    /// the setting while the app was suspended or not in focus.
    /// </summary>
    /// <returns>True, if the microphone is available.</returns>
    public async static Task<bool> RequestMicrophonePermission()
    {
        try
        {
            // Request access to the audio capture device.
            MediaCaptureInitializationSettings settings = new MediaCaptureInitializationSettings();
            settings.StreamingCaptureMode = StreamingCaptureMode.Audio;
            settings.MediaCategory = MediaCategory.Speech;
            MediaCapture capture = new MediaCapture();

            await capture.InitializeAsync(settings);
        }
        catch (TypeLoadException)
        {
            // Thrown when a media player is not available.
            var messageDialog = new Windows.UI.Popups.MessageDialog("Media player components are unavailable.");
            await messageDialog.ShowAsync();
            return false;
        }
        catch (UnauthorizedAccessException)
        {
            // Thrown when permission to use the audio capture device is denied.
            // If this occurs, show an error or disable recognition functionality.
            return false;
        }
        catch (Exception exception)
        {
            // Thrown when an audio capture device is not present.
            if (exception.HResult == NoCaptureDevicesHResult)
            {
                var messageDialog = new Windows.UI.Popups.MessageDialog("No Audio Capture devices are present on this system.");
                await messageDialog.ShowAsync();
                return false;
            }
            else
            {
                throw;
            }
        }
        return true;
    }
}
```

```cpp
/// <summary>
/// Note that this method only checks the Settings->Privacy->Microphone setting, it does not handle
/// the Cortana/Dictation privacy check.
///
/// You should perform this check every time the app gets focus, in case the user has changed
/// the setting while the app was suspended or not in focus.
/// </summary>
/// <returns>True, if the microphone is available.</returns>
IAsyncOperation<bool>^  AudioCapturePermissions::RequestMicrophonePermissionAsync()
{
    return create_async([]() 
    {
        try
        {
            // Request access to the audio capture device.
            MediaCaptureInitializationSettings^ settings = ref new MediaCaptureInitializationSettings();
            settings->StreamingCaptureMode = StreamingCaptureMode::Audio;
            settings->MediaCategory = MediaCategory::Speech;
            MediaCapture^ capture = ref new MediaCapture();

            return create_task(capture->InitializeAsync(settings))
                .then([](task<void> previousTask) -> bool
            {
                try
                {
                    previousTask.get();
                }
                catch (AccessDeniedException^)
                {
                    // Thrown when permission to use the audio capture device is denied.
                    // If this occurs, show an error or disable recognition functionality.
                    return false;
                }
                catch (Exception^ exception)
                {
                    // Thrown when an audio capture device is not present.
                    if (exception->HResult == AudioCapturePermissions::NoCaptureDevicesHResult)
                    {
                        auto messageDialog = ref new Windows::UI::Popups::MessageDialog("No Audio Capture devices are present on this system.");
                        create_task(messageDialog->ShowAsync());
                        return false;
                    }

                    throw;
                }
                return true;
            });
        }
        catch (Platform::ClassNotRegisteredException^ ex)
        {
            // Thrown when a media player is not available. 
            auto messageDialog = ref new Windows::UI::Popups::MessageDialog("Media Player Components unavailable.");
            create_task(messageDialog->ShowAsync());
            return create_task([] {return false; });
        }
    });
}
```

```js
var AudioCapturePermissions = WinJS.Class.define(
    function () { }, {},
    {
        requestMicrophonePermission: function () {
            /// <summary>
            /// Note that this method only checks the Settings->Privacy->Microphone setting, it does not handle
            /// the Cortana/Dictation privacy check.
            ///
            /// You should perform this check every time the app gets focus, in case the user has changed
            /// the setting while the app was suspended or not in focus.
            /// </summary>
            /// <returns>True, if the microphone is available.</returns>
            return new WinJS.Promise(function (completed, error) {

                try {
                    // Request access to the audio capture device.
                    var captureSettings = new Windows.Media.Capture.MediaCaptureInitializationSettings();
                    captureSettings.streamingCaptureMode = Windows.Media.Capture.StreamingCaptureMode.audio;
                    captureSettings.mediaCategory = Windows.Media.Capture.MediaCategory.speech;

                    var capture = new Windows.Media.Capture.MediaCapture();
                    capture.initializeAsync(captureSettings).then(function () {
                        completed(true);
                    },
                    function (error) {
                        // Audio Capture can fail to initialize if there's no audio devices on the system, or if
                        // the user has disabled permission to access the microphone in the Privacy settings.
                        if (error.number == -2147024891) { // Access denied (microphone disabled in settings)
                            completed(false);
                        } else if (error.number == -1072845856) { // No recording device present.
                            var messageDialog = new Windows.UI.Popups.MessageDialog("No Audio Capture devices are present on this system.");
                            messageDialog.showAsync();
                            completed(false);
                        } else {
                            error(error);
                        }
                    });
                } catch (exception) {
                    if (exception.number == -2147221164) { // REGDB_E_CLASSNOTREG
                        var messageDialog = new Windows.UI.Popups.MessageDialog("Media Player components not available on this system.");
                        messageDialog.showAsync();
                        return false;
                    }
                }
            });
        }
    })
```

## <a name="recognize-speech-input"></a><span data-ttu-id="50acf-116">Erkennen von Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="50acf-116">Recognize speech input</span></span>

<span data-ttu-id="50acf-117">Mit einer *Einschränkung* werden die Wörter und Wortgruppen (Vokabular) definiert, die eine App bei der Spracheingabe erkennt.</span><span class="sxs-lookup"><span data-stu-id="50acf-117">A *constraint* defines the words and phrases (vocabulary) that an app recognizes in speech input.</span></span> <span data-ttu-id="50acf-118">Einschränkungen sind der Kern der Spracherkennung und verleihen Ihrer App mehr Kontrolle über die Genauigkeit der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="50acf-118">Constraints are at the core of speech recognition and give your app greater over the accuracy of speech recognition.</span></span>

<span data-ttu-id="50acf-119">Sie können die folgenden Arten von Einschränkungen für die Erkennung von Spracheingabe verwenden.</span><span class="sxs-lookup"><span data-stu-id="50acf-119">You can use the following types of constraints for recognizing speech input.</span></span>

### <a name="predefined-grammars"></a><span data-ttu-id="50acf-120">Vordefinierte Grammatiken</span><span class="sxs-lookup"><span data-stu-id="50acf-120">Predefined grammars</span></span>

<span data-ttu-id="50acf-121">Mit vordefinierten Diktier- und Websuchgrammatiken können Sie eine Spracherkennung für Ihre App bereitstellen, ohne eine Grammatik erstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="50acf-121">Predefined dictation and web-search grammars provide speech recognition for your app without requiring you to author a grammar.</span></span> <span data-ttu-id="50acf-122">Bei Verwendung dieser Grammatiken wird die Spracherkennung von einem Remotewebdienst durchgeführt, und die Ergebnisse werden an das Gerät zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="50acf-122">When using these grammars, speech recognition is performed by a remote web service and the results are returned to the device.</span></span>

<span data-ttu-id="50acf-123">Die Standardgrammatik der Freitext-Diktierfunktion erkennt die meisten Wörter und Ausdrücke, die Benutzer in einer bestimmten Sprache sagen können, und ist für die Erkennung kurzer Ausdrücke optimiert.</span><span class="sxs-lookup"><span data-stu-id="50acf-123">The default free-text dictation grammar can recognize most words and phrases that a user can say in a particular language, and is optimized to recognize short phrases.</span></span> <span data-ttu-id="50acf-124">Die vordefinierte Grammatik für das Diktieren kommt dann zum Einsatz, wenn Sie keine Einschränkungen für Ihr [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226)-Objekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="50acf-124">The predefined dictation grammar is used if you don't specify any constraints for your [**SpeechRecognizer**](https://msdn.microsoft.com/library/windows/apps/dn653226) object.</span></span> <span data-ttu-id="50acf-125">Die Freitext-Diktierfunktion ist nützlich, wenn Sie nicht einschränken möchten, was Benutzer sagen können.</span><span class="sxs-lookup"><span data-stu-id="50acf-125">Free-text dictation is useful when you don't want to limit the kinds of things a user can say.</span></span> <span data-ttu-id="50acf-126">Typische Verwendungsmöglichkeiten sind das Erstellen von Notizen oder das Diktieren eines Nachrichtentexts.</span><span class="sxs-lookup"><span data-stu-id="50acf-126">Typical uses include creating notes or dictating the content for a message.</span></span>

<span data-ttu-id="50acf-127">Die Grammatik für die Websuche enthält wie die Diktiergrammatik eine große Anzahl von Wörtern und Ausdrücken, die Benutzer sagen können.</span><span class="sxs-lookup"><span data-stu-id="50acf-127">The web-search grammar, like a dictation grammar, contains a large number of words and phrases that a user might say.</span></span> <span data-ttu-id="50acf-128">Sie ist allerdings für die Erkennung von Begriffen optimiert, die beim Suchen im Web häufig verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="50acf-128">However, it is optimized to recognize terms that people typically use when searching the web.</span></span>

<span data-ttu-id="50acf-129">**Hinweis:** da vordefinierte Diktier- und Websuche Grammatiken groß sein können und diese online sind (nicht auf dem Gerät), Leistung ist möglicherweise nicht so gut wie bei einer lokal auf dem Gerät installierten benutzerdefinierten Grammatik.</span><span class="sxs-lookup"><span data-stu-id="50acf-129">**Note**Because predefined dictation and web-search grammars can be large, and because they are online (not on the device), performance might not be as fast as with a custom grammar installed on the device.</span></span>     

<span data-ttu-id="50acf-130">Diese vordefinierten Grammatiken können zum Erkennen von bis zu zehn Sekunden Spracheingabe verwendet werden. Sie müssen dazu keinen Code selbst erstellen.</span><span class="sxs-lookup"><span data-stu-id="50acf-130">These predefined grammars can be used to recognize up to 10 seconds of speech input and require no authoring effort on your part.</span></span> <span data-ttu-id="50acf-131">Sie erfordern jedoch eine Netzwerkverbindung.</span><span class="sxs-lookup"><span data-stu-id="50acf-131">However, they do require a connection to a network.</span></span>

<span data-ttu-id="50acf-132">Zum Verwenden der Webdiensteinschränkungen muss die Unterstützung für die Spracheingabe und das Diktieren unter **Einstellungen** **-> Datenschutz -> Datenschutzeinstellungen für Sprache, Freihand, Eingabe** aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="50acf-132">To use web-service constraints, speech input and dictation support must be enabled in **Settings** by turning on the "Get to know me" option in  **Settings -> Privacy -> Speech, inking, and typing**.</span></span>

<span data-ttu-id="50acf-133">Hier wird erläutert, wie Sie testen, ob die Spracheingabe aktiviert ist, und wie Sie die Seite „Einstellungen -> Datenschutz -> Datenschutzeinstellungen für Sprache, Freihand und Eingabe“ öffnen.</span><span class="sxs-lookup"><span data-stu-id="50acf-133">Here, we show how to test whether speech input is enabled and open the Settings -> Privacy -> Speech, inking, and typing page, if not.</span></span>

<span data-ttu-id="50acf-134">Zuerst initialisieren wir eine globale Variable (HResultPrivacyStatementDeclined) für den HResult-Wert 0x80045509.</span><span class="sxs-lookup"><span data-stu-id="50acf-134">First, we initialize a global variable (HResultPrivacyStatementDeclined) to the HResult value of 0x80045509.</span></span> <span data-ttu-id="50acf-135">Weitere Informationen finden Sie unter [Ausnahmebehandlung in C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/dn532194).</span><span class="sxs-lookup"><span data-stu-id="50acf-135">See [Exception handling for in C\# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/dn532194).</span></span>

```csharp
private static uint HResultPrivacyStatementDeclined = 0x80045509;
```

<span data-ttu-id="50acf-136">Anschließend fangen wir während der Erkennung alle standardmäßigen Ausnahmen ab und testen, ob der [**HResult**](https://msdn.microsoft.com/library/windows/apps/br206579)-Wert dem Wert der HResultPrivacyStatementDeclined-Variablen entspricht.</span><span class="sxs-lookup"><span data-stu-id="50acf-136">We then catch any standard exceptions during recogntion and test if the [**HResult**](https://msdn.microsoft.com/library/windows/apps/br206579) value is equal to the value of the HResultPrivacyStatementDeclined variable.</span></span> <span data-ttu-id="50acf-137">Wenn ja, zeigen wir eine Warnung an und rufen `await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-accounts"));` auf, um die Seite „Einstellungen“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="50acf-137">If so, we display a warning and call `await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-accounts"));` to open the Settings page.</span></span>

```csharp
catch (Exception exception)
{
  // Handle the speech privacy policy error.
  if ((uint)exception.HResult == HResultPrivacyStatementDeclined)
  {
    resultTextBlock.Visibility = Visibility.Visible;
    resultTextBlock.Text = "The privacy statement was declined." + 
      "Go to Settings -> Privacy -> Speech, inking and typing, and ensure you" +
      "have viewed the privacy policy, and 'Get To Know You' is enabled.";
    // Open the privacy/speech, inking, and typing settings page.
    await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-accounts")); 
  }
  else
  {
    var messageDialog = new Windows.UI.Popups.MessageDialog(exception.Message, "Exception");
    await messageDialog.ShowAsync();
  }
}
```

<span data-ttu-id="50acf-138">Finden Sie unter [**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446).</span><span class="sxs-lookup"><span data-stu-id="50acf-138">See [**SpeechRecognitionTopicConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631446).</span></span>

### <a name="programmatic-list-constraints"></a><span data-ttu-id="50acf-139">Einschränkungen per programmgesteuerter Liste</span><span class="sxs-lookup"><span data-stu-id="50acf-139">Programmatic list constraints</span></span> 

<span data-ttu-id="50acf-140">Einschränkungen per programmgesteuerter Liste sind eine unkomplizierte Methode für die Erstellung einfacher Grammatiken in Form einer Liste von Wörtern und Ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="50acf-140">Programmatic list constraints provide a lightweight approach to creating simple grammars using a list of words or phrases.</span></span> <span data-ttu-id="50acf-141">Eine Einschränkungsliste eignet sich gut für die Erkennung kurzer, einzelner Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="50acf-141">A list constraint works well for recognizing short, distinct phrases.</span></span> <span data-ttu-id="50acf-142">Das explizite Angeben aller Wörter in einer Grammatik verbessert auch die Erkennungsgenauigkeit, da das Spracherkennungsmodul nur eine Übereinstimmung bestätigen muss.</span><span class="sxs-lookup"><span data-stu-id="50acf-142">Explicitly specifying all words in a grammar also improves recognition accuracy, as the speech recognition engine must only process speech to confirm a match.</span></span> <span data-ttu-id="50acf-143">Die Liste kann auch programmgesteuert aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="50acf-143">The list can also be programmatically updated.</span></span>

<span data-ttu-id="50acf-144">Eine Einschränkungsliste besteht aus einem Array von Zeichenfolgen, die die Spracheingaben darstellen, die von Ihrer App für einen Erkennungsvorgang akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="50acf-144">A list constraint consists of an array of strings that represents speech input that your app will accept for a recognition operation.</span></span> <span data-ttu-id="50acf-145">Sie können in Ihrer App eine Einschränkungsliste einrichten, indem Sie ein Einschränkungslistenobjekt für die Spracherkennung erstellen und ein Array mit Zeichenfolgen übergeben.</span><span class="sxs-lookup"><span data-stu-id="50acf-145">You can create a list constraint in your app by creating a speech-recognition list-constraint object and passing an array of strings.</span></span> <span data-ttu-id="50acf-146">Fügen Sie dieses Objekt dann der Einschränkungsauflistung der Erkennung hinzu.</span><span class="sxs-lookup"><span data-stu-id="50acf-146">Then, add that object to the constraints collection of the recognizer.</span></span> <span data-ttu-id="50acf-147">Die Erkennung ist erfolgreich, wenn die Spracherkennung die Zeichenfolgen des Arrays erkennt.</span><span class="sxs-lookup"><span data-stu-id="50acf-147">Recognition is successful when the speech recognizer recognizes any one of the strings in the array.</span></span>

<span data-ttu-id="50acf-148">Finden Sie unter [**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421).</span><span class="sxs-lookup"><span data-stu-id="50acf-148">See [**SpeechRecognitionListConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631421).</span></span>

### <a name="srgs-grammars"></a><span data-ttu-id="50acf-149">SRGS-Grammatik</span><span class="sxs-lookup"><span data-stu-id="50acf-149">SRGS grammars</span></span>

<span data-ttu-id="50acf-150">Eine Speech Recognition Grammar Specification (SRGS)-Grammatik ist ein statisches Dokument, das im Gegensatz zu einer Einschränkung per programmgesteuerter Liste das in [SRGS Version1.0](https://go.microsoft.com/fwlink/p/?LinkID=262302) definierte XML-Format verwendet.</span><span class="sxs-lookup"><span data-stu-id="50acf-150">An Speech Recognition Grammar Specification (SRGS) grammar is a static document that, unlike a programmatic list constraint, uses the XML format defined by the [SRGS Version 1.0](https://go.microsoft.com/fwlink/p/?LinkID=262302).</span></span> <span data-ttu-id="50acf-151">Eine SRGS-Grammatik bietet die höchstmögliche Kontrolle über die Spracherkennungsfunktion, da Sie mehrere semantische Bedeutungen in einem einzigen Erkennungsvorgang erfassen können.</span><span class="sxs-lookup"><span data-stu-id="50acf-151">An SRGS grammar provides the greatest control over the speech recognition experience by letting you capture multiple semantic meanings in a single recognition.</span></span>

 <span data-ttu-id="50acf-152">Finden Sie unter [**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412).</span><span class="sxs-lookup"><span data-stu-id="50acf-152">See [**SpeechRecognitionGrammarFileConstraint**](https://msdn.microsoft.com/library/windows/apps/dn631412).</span></span>

### <a name="voice-command-constraints"></a><span data-ttu-id="50acf-153">Einschränkungen für Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="50acf-153">Voice command constraints</span></span>

<span data-ttu-id="50acf-154">Verwenden Sie eine Voice Command Definition-(VCD-)XML-Datei, um die Befehle zu definieren, mit denen der Benutzer Aktionen initiieren kann, wenn er Ihre App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="50acf-154">Use a Voice Command Definition (VCD) XML file to define the commands that the user can say to initiate actions when activating your app.</span></span> <span data-ttu-id="50acf-155">Weitere Details finden Sie unter [Starten einer Vordergrund-App mit Sprachbefehlen in Cortana](https://msdn.microsoft.com/cortana/voicecommands/launch-a-foreground-app-with-voice-commands-in-cortana).</span><span class="sxs-lookup"><span data-stu-id="50acf-155">For more detail, see [Launch a foreground app with voice commands in Cortana](https://msdn.microsoft.com/cortana/voicecommands/launch-a-foreground-app-with-voice-commands-in-cortana).</span></span>

<span data-ttu-id="50acf-156">Finden Sie unter [ **SpeechRecognitionVoiceCommandDefinitionConstraint**](https://msdn.microsoft.com/library/windows/apps/dn653220)/</span><span class="sxs-lookup"><span data-stu-id="50acf-156">See [**SpeechRecognitionVoiceCommandDefinitionConstraint**](https://msdn.microsoft.com/library/windows/apps/dn653220)/</span></span>

<span data-ttu-id="50acf-157">**Hinweis:** der Typ der Einschränkung, den Sie verwenden, hängt von der Komplexität der Erkennungsfunktion, die Sie erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="50acf-157">**Note**The type of constraint type you use depends on the complexity of the recognition experience you want to create.</span></span> <span data-ttu-id="50acf-158">Für eine bestimmte Erkennungsaufgabe kann jeweils einer der Ansätze am besten geeignet sein, und vielleicht haben Sie in Ihrer App sogar für alle Einschränkungsarten Verwendung.</span><span class="sxs-lookup"><span data-stu-id="50acf-158">Any could be the best choice for a specific recognition task, and you might find uses for all types of constraints in your app.</span></span>
<span data-ttu-id="50acf-159">Informationen zu den ersten Schritten mit Einschränkungen finden Sie unter [Definieren von benutzerdefinierten Erkennungseinschränkungen](define-custom-recognition-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="50acf-159">To get started with constraints, see [Define custom recognition constraints](define-custom-recognition-constraints.md).</span></span>

<span data-ttu-id="50acf-160">Die vordefinierte Diktiergrammatik von universellen Windows-Apps erkennt die meisten Wörter und kurzen Wortgruppen einer Sprache.</span><span class="sxs-lookup"><span data-stu-id="50acf-160">The predefined Universal Windows app dictation grammar recognizes most words and short phrases in a language.</span></span> <span data-ttu-id="50acf-161">Sie wird standardmäßig aktiviert, wenn ein Spracherkennungsobjekt ohne benutzerdefinierte Einschränkungen instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="50acf-161">It is activated by default when a speech recognizer object is instantiated without custom constraints.</span></span>

<span data-ttu-id="50acf-162">In diesem Beispiel zeigen wir Ihnen, wie Sie:</span><span class="sxs-lookup"><span data-stu-id="50acf-162">In this example, we show how to:</span></span>

- <span data-ttu-id="50acf-163">eine Spracherkennung erstellen,</span><span class="sxs-lookup"><span data-stu-id="50acf-163">Create a speech recognizer.</span></span>
- <span data-ttu-id="50acf-164">die standardmäßigen Einschränkungen von universellen Windows-Apps kompilieren (es wurde keine Grammatik zum Grammatiksatz der Spracherkennung hinzugefügt) und</span><span class="sxs-lookup"><span data-stu-id="50acf-164">Compile the default Universal Windows app constraints (no grammars have been added to the speech recognizer's grammar set).</span></span>
- <span data-ttu-id="50acf-165">die Spracherkennung starten, indem Sie die einfache Erkennungs-UI und das TTS-Feedback der [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245)-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="50acf-165">Start listening for speech by using the basic recognition UI and TTS feedback provided by the [**RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) method.</span></span> <span data-ttu-id="50acf-166">Verwenden Sie die [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244)-Methode, wenn die Standard-UI nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="50acf-166">Use the [**RecognizeAsync**](https://msdn.microsoft.com/library/windows/apps/dn653244) method if the default UI is not required.</span></span>

```CSharp
private async void StartRecognizing_Click(object sender, RoutedEventArgs e)
{
    // Create an instance of SpeechRecognizer.
    var speechRecognizer = new Windows.Media.SpeechRecognition.SpeechRecognizer();

    // Compile the dictation grammar by default.
    await speechRecognizer.CompileConstraintsAsync();

    // Start recognition.
    Windows.Media.SpeechRecognition.SpeechRecognitionResult speechRecognitionResult = await speechRecognizer.RecognizeWithUIAsync();

    // Do something with the recognition result.
    var messageDialog = new Windows.UI.Popups.MessageDialog(speechRecognitionResult.Text, "Text spoken");
    await messageDialog.ShowAsync();
}
```

## <a name="customize-the-recognition-ui"></a><span data-ttu-id="50acf-167">Anpassen der Erkennungs-UI</span><span class="sxs-lookup"><span data-stu-id="50acf-167">Customize the recognition UI</span></span>


<span data-ttu-id="50acf-168">Wenn Ihre App die Spracherkennung durch Aufruf von [**SpeechRecognizer.RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245) zu leisten versucht, werden mehrere Bildschirme in der folgenden Reihenfolge angezeigt.</span><span class="sxs-lookup"><span data-stu-id="50acf-168">When your app attempts speech recognition by calling [**SpeechRecognizer.RecognizeWithUIAsync**](https://msdn.microsoft.com/library/windows/apps/dn653245), several screens are shown in the following order.</span></span>

<span data-ttu-id="50acf-169">Wenn Sie eine Einschränkung auf der Grundlage einer vordefinierten Grammatik (Diktat oder Websuche) verwenden:</span><span class="sxs-lookup"><span data-stu-id="50acf-169">If you're using a constraint based on a predefined grammar (dictation or web search):</span></span>

-   <span data-ttu-id="50acf-170">Der Bildschirm **Spracherkennung**</span><span class="sxs-lookup"><span data-stu-id="50acf-170">The **Listening** screen.</span></span>
-   <span data-ttu-id="50acf-171">Der Bildschirm **Verarbeitung**</span><span class="sxs-lookup"><span data-stu-id="50acf-171">The **Thinking** screen.</span></span>
-   <span data-ttu-id="50acf-172">Der Bildschirm **Gehört** oder der Fehlerbildschirm</span><span class="sxs-lookup"><span data-stu-id="50acf-172">The **Heard you say** screen or the error screen.</span></span>

<span data-ttu-id="50acf-173">Wenn Sie eine Einschränkung auf der Grundlage von Wörtern oder Ausdrücken oder eine Einschränkung auf der Grundlage einer SRGS-Grammatikdatei verwenden:</span><span class="sxs-lookup"><span data-stu-id="50acf-173">If you're using a constraint based on a list of words or phrases, or a constraint based on a SRGS grammar file:</span></span>

-   <span data-ttu-id="50acf-174">Der Bildschirm **Spracherkennung**</span><span class="sxs-lookup"><span data-stu-id="50acf-174">The **Listening** screen.</span></span>
-   <span data-ttu-id="50acf-175">Der Bildschirm **Sagten Sie** , falls die vom Benutzer ausgesprochenen Wörter als mehrere potenzielle Ergebnisse interpretiert werden können.</span><span class="sxs-lookup"><span data-stu-id="50acf-175">The **Did you say** screen, if what the user said could be interpreted as more than one potential result.</span></span>
-   <span data-ttu-id="50acf-176">Der Bildschirm **Gehört** oder der Fehlerbildschirm</span><span class="sxs-lookup"><span data-stu-id="50acf-176">The **Heard you say** screen or the error screen.</span></span>

<span data-ttu-id="50acf-177">Die folgende Abbildung zeigt ein Beispiel für den Fluss zwischen Bildschirmen für die Spracherkennung mit einer Einschränkung auf der Grundlage einer SRGS-Grammatikdatei.</span><span class="sxs-lookup"><span data-stu-id="50acf-177">The following image shows an example of the flow between screens for a speech recognizer that uses a constraint based on a SRGS grammar file.</span></span> <span data-ttu-id="50acf-178">In diesem Beispiel war die Spracherkennung erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="50acf-178">In this example, speech recognition was successful.</span></span>

![initial Erkennung screen for a constraint based on a sgrs grammar file](images/speech-listening-initial.png)

![intermediate Erkennung screen for a constraint based on a sgrs grammar file](images/speech-listening-intermediate.png)

![final Erkennung screen for a constraint based on a sgrs grammar file](images/speech-listening-complete.png)

<span data-ttu-id="50acf-182">Der **Spracherkennung**-Bildschirm kann Beispiele für Wörter oder Ausdrücke zur Erkennung durch die App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="50acf-182">The **Listening** screen can provide examples of words or phrases that the app can recognize.</span></span> <span data-ttu-id="50acf-183">Hier zeigen wir, wie Sie die Eigenschaften der [**SpeechRecognizerUIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653234)-Klasse (abgerufen durch Aufrufen der [**SpeechRecognizer.UIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653254)-Eigenschaft) zur Anpassung von Inhalten auf dem **Spracherkennung**-Bildschirm verwenden.</span><span class="sxs-lookup"><span data-stu-id="50acf-183">Here, we show how to use the properties of the [**SpeechRecognizerUIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653234) class (obtained by calling the [**SpeechRecognizer.UIOptions**](https://msdn.microsoft.com/library/windows/apps/dn653254) property) to customize content on the **Listening** screen.</span></span>

```CSharp
private async void WeatherSearch_Click(object sender, RoutedEventArgs e)
{
    // Create an instance of SpeechRecognizer.
    var speechRecognizer = new Windows.Media.SpeechRecognition.SpeechRecognizer();

    // Listen for audio input issues.
    speechRecognizer.RecognitionQualityDegrading += speechRecognizer_RecognitionQualityDegrading;

    // Add a web search grammar to the recognizer.
    var webSearchGrammar = new Windows.Media.SpeechRecognition.SpeechRecognitionTopicConstraint(Windows.Media.SpeechRecognition.SpeechRecognitionScenario.WebSearch, "webSearch");


    speechRecognizer.UIOptions.AudiblePrompt = "Say what you want to search for...";
    speechRecognizer.UIOptions.ExampleText = @"Ex. 'weather for London'";
    speechRecognizer.Constraints.Add(webSearchGrammar);

    // Compile the constraint.
    await speechRecognizer.CompileConstraintsAsync();

    // Start recognition.
    Windows.Media.SpeechRecognition.SpeechRecognitionResult speechRecognitionResult = await speechRecognizer.RecognizeWithUIAsync();
    //await speechRecognizer.RecognizeWithUIAsync();

    // Do something with the recognition result.
    var messageDialog = new Windows.UI.Popups.MessageDialog(speechRecognitionResult.Text, "Text spoken");
    await messageDialog.ShowAsync();
}
```

## <a name="related-articles"></a><span data-ttu-id="50acf-184">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="50acf-184">Related articles</span></span>


**<span data-ttu-id="50acf-185">Entwickler</span><span class="sxs-lookup"><span data-stu-id="50acf-185">Developers</span></span>**
* <span data-ttu-id="50acf-186">[Interaktionen mit der Spracherkennung](speech-interactions.md)
**Designer**</span><span class="sxs-lookup"><span data-stu-id="50acf-186">[Speech interactions](speech-interactions.md)
**Designers**</span></span>
* <span data-ttu-id="50acf-187">[Entwicklungsrichtlinien für die Spracherkennung](https://msdn.microsoft.com/library/windows/apps/dn596121)
**Beispiele**</span><span class="sxs-lookup"><span data-stu-id="50acf-187">[Speech design guidelines](https://msdn.microsoft.com/library/windows/apps/dn596121)
**Samples**</span></span>
* [<span data-ttu-id="50acf-188">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="50acf-188">Speech recognition and speech synthesis sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




