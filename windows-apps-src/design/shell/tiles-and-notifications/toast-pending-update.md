---
author: andrewleader
Description: Learn how to create multi-step interactions in your notifications.
title: Popups mit ausstehenden Updates in Aktion
label: Toast with pending update activation
template: detail.hbs
ms.author: mijacobs
ms.date: 12/14/2017
ms.topic: article
keywords: Windows10, UWP, Popup, ausstehende Updates, ausstehendes Update, Interaktivität aus mehreren Schritten, Interaktivitäten aus mehreren Schritten
ms.localizationpriority: medium
ms.openlocfilehash: 4d21c96676eec1b8b1a1f4397880af937dd8f4b6
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7300944"
---
# <a name="toast-with-pending-update-activation"></a>Popups mit ausstehenden Updates in Aktion

Verwenden Sie das **PendingUpdate** zum Erstellen der Interaktivität aus mehreren Schritten innerhalb Ihrer Popups. Beispielsweise können Sie, wie unten dargestellt, eine Reihe von Popups erstellen, deren Antworten von den vorherigen Popups der nachfolgenden Popupbenachrichtigungen abhängt.

![Popup mit ausstehendem Update](images/toast-pendingupdate.gif)

> [!IMPORTANT]
> **Erfordert Desktop Creators Update und 2.0.0 der Benachrichtigungsbibliothek**: Sie müssen Desktop Build 16299 oder höher ausführen, um ausstehende Updates zu sehen. Sie müssen Version 2.0.0 oder höher der [UWP Community Toolkit Benachrichtigungen NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um **PendingUpdate** auf Ihre Schaltflächen anzuwenden. **PendingUpdate** wird nur auf Desktop unterstützt und auf anderen Geräten ignoriert.


## <a name="prerequisites"></a>Voraussetzungen

Dieser Artikel erfordert Grundkenntnisse in...

- [Erstellen von Popupinhalt](adaptive-interactive-toasts.md)
- [Senden von Popups und behandeln der Hintergrundaktivierung](send-local-toast.md)


## <a name="overview"></a>Übersicht

Um ein Popup zu implementieren, das „ausstehende Updates” als Verhalten nach der Aktivierung verwendet...

1. Geben Sie auf den Schaltflächen für die Hintergrundaktivierung ein **AfterActivationBehavior** des **PendingUpdate** an

2. Weisen Sie beim Senden Ihrer Popups einen **Tag** (und optional eine **Gruppe**) hinzu

3. Wenn der Benutzer die Schaltfläche anklickt, wird die Hintergrundaufgabe aktiviert und das Popup auf dem Bildschirm in einem Zustand des ausstehenden Updates beibehalten

4. Senden Sie in Ihrer Hintergrundaufgabe eine neue Popupbenachrichtigung mit dem neuen Inhalt, mit dem gleichen **Tag** und der **Gruppe**


## <a name="assign-pendingupdate"></a>Zuweisen von PendingUpdate

Setzen Sie auf den Schaltflächen für die Hintergrundaktivierung das **AfterActivationBehavior** auf **PendingUpdate**. Beachten Sie, dass dies nur für Schaltflächen funktioniert, die einen **ActivationType** im **Hintergrund** habe.

```csharp
new ToastButton("Yes", "action=orderLunch")
{
    ActivationType = ToastActivationType.Background,

    ActivationOptions = new ToastActivationOptions()
    {
        AfterActivationBehavior = ToastAfterActivationBehavior.PendingUpdate
    }
}
```

```xml
<action
    content='Yes'
    arguments='action=orderLunch'
    activationType='background'
    afterActivationBehavior='pendingUpdate' />
```


## <a name="use-a-tag-on-the-notification"></a>Verwenden Sie ein Tag auf der Benachrichtigung

Um die Benachrichtigung später zu ersetzen, müssen wir den **Tag** (und optional die **Gruppe**) auf die Benachrichtigung zuweisen.

```csharp
// Create the notification
var notif = new ToastNotification(content.GetXml())
{
    Tag = "lunch"
};

// And show it
ToastNotificationManager.CreateToastNotifier().Show(notif);
```


## <a name="replace-the-toast-with-new-content"></a>Ersetzen Sie das Popup mit neuem Inhalt

Wenn der Benutzer auf die Schaltfläche klickt, wird die Hintergrundaufgabe ausgelöst, und das Popup muss durch neuen Inhalt ersetzt werden. Ersetzen Sie das Popup durch Senden einer neuen Popupbenachrichtigung mit den gleichen **Tag** und der gleichen **Gruppe**.

Es wird dringend empfohlen, als Antwort auf eine angeklickte Schaltfläche die **Audiowiedergabe auf lautlos festzulegen**, da der Benutzer bereits mit Ihrem Popup interagiert.

```csharp
// Generate new content
ToastContent content = new ToastContent()
{
    ...

    // We disable audio on all subsequent toasts since they appear right after the user
    // clicked something, so the user's attention is already captured
    Audio = new ToastAudio() { Silent = true }
};

// Create the new notification
var notif = new ToastNotification(content.GetXml())
{
    Tag = "lunch"
};

// And replace the old one with this one
ToastNotificationManager.CreateToastNotifier().Show(notif);
```


## <a name="related-topics"></a>Verwandte Themen

- [Vollständiges Codebeispiel auf GitHub](https://github.com/WindowsNotifications/quickstart-toast-pending-update)
- [Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung](send-local-toast.md)
- [Dokumentation zu Popupinhalt](adaptive-interactive-toasts.md)
- [Popup-Statusanzeige](toast-progress-bar.md)