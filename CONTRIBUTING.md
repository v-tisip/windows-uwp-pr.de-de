# <a name="contributing-to-uwp-conceptual-documentation"></a>Beitragen zur UWP-Konzeptdokumentation

Vielen Dank für Ihr Interesse an der Dokumentation zur Universellen Windows-Plattform (UWP)! Wir freuen uns über Ihr Feedback, Änderungen und Ergänzungen unserer Dokumente.

Auf dieser Seite werden die grundlegenden Schritte für Ihren Beitrag zu unserer Entwicklerdokumentation behandelt.

## <a name="public-and-private-repos"></a>Öffentliche und private Repositorys

Die UWP-Konzeptdokumentation befindet sich in zwei unterschiedlichen Repositorys, die dann in einer einzelnen Website zusammengeführt und aktualisiert werden: ein Repository ist für Beiträge beliebiger Personen und das andere nur für Microsoft-Mitarbeiter vorgesehen.

Wenn Sie ***kein*** Microsoft-Mitarbeiter sind, verwenden Sie das [öffentliche Repository](https://github.com/MicrosoftDocs/windows-uwp).

Wenn Sie Microsoft-Mitarbeiter ***sind***, können Sie entweder das öffentliche Repository oder das [private Repository](https://cpubwin.visualstudio.com/_git/windows-uwp) verwenden. Mitarbeiter können Änderungen über das private Repository etwas schneller online stellen oder einen [bestimmten Zweig](https://review.docs.microsoft.com/en-us/windows-authoring-guide/uwp/conceptual/setup-local-repo-for-large-changes#what-branch-should-i-use-for-my-authoring) für Änderungen verwenden, die bis zu einem späteren Zeitpunkt unter Verschluss bleiben müssen.

## <a name="editing-topics-on-the-public-repo"></a>Bearbeiten von Themen für das öffentliche Repository

Wir haben versucht, die Bearbeitung einer vorhandenen Datei so einfach wie möglich zu gestalten. 
- Wenn Sie das Repository bereits geöffnet haben, navigieren Sie zu der gewünschten Datei, und klicken Sie auf die Schaltfläche **Edit**.  
- Wenn Sie die Seite „Docs.microsoft.com“ in Ihrem Browser anzeigen, können Sie alternativ rechts oben auf die Schaltfläche **Edit** klicken. Sie werden zur richtigen Markdown-Quelldatei im Repository umgeleitet, in dem Sie auf die Schaltfläche **Edit** klicken können. 

GitHub verzweigt das offizielle Repository automatisch in Ihr persönliches GitHub-Konto, in dem Sie Ihre Änderungen vornehmen können. Wenn Sie fertig sind, übermitteln Sie eine Pull-Anforderung an den Zweig „docs“. Nachdem Sie die Pull-Anforderung erstellt haben, überprüft ein Mitglied des UWP-Dokumentationsteams Ihre Änderungen. Wenn Ihre Anforderung akzeptiert wird, werden Aktualisierungen auf https://docs.microsoft.com/Windows/ veröffentlicht.

Sie können die Grundlagen des Markdown in nur wenigen Minuten erlernen.  Sehen Sie sich zunächst die Seite [Mastering Markdown](https://guides.github.com/features/mastering-markdown/) an.

## <a name="making-more-substantial-changes"></a>Vornehmen größerer Änderungen

Um größere Änderungen an einem vorhandenen Artikel vorzunehmen, Bilder hinzufügen oder zu ändern oder einen neuen Artikel zu schreiben, müssen Sie einen lokalen Klon unseres privaten Inhalts-Repository erstellen. Befolgen Sie die [Anweisungen in unserem Windows-Erstellungshandbuch](https://review.docs.microsoft.com/en-us/windows-authoring-guide/uwp/conceptual/). Wenn Sie noch kein GitHub-Konto eingerichtet und Ihren Microsoft-Alias noch keiner Domänen zugeordnet haben, [beginnen Sie hier](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account).

## <a name="using-issues-to-provide-feedback-on-uwp-conceptual-documentation"></a>Verwendung von Problemen zum Bereitstellen von Feedback für die UWP-Konzeptdokumentation

Wenn Sie nur Feedback bereitstellen möchten, anstatt die Dokumentationsseiten tatsächlich zu ändern, können Sie [im öffentlichen Repository ein Problem erstellen](https://github.com/MicrosoftDocs/windows-uwp/issues). Klicken Sie auf die Registerkarte „Issues“, und klicken Sie dann auf die Schaltfläche **New issue**. Vergessen Sie nicht, den Titel des Themas und die URL für die Seite anzugeben.

Mitglieder des UWP-Dokumentationsteams überprüfen regelmäßig die Probleme, sichten sie, ordnen sie zu und beheben sie entsprechend.

*Verwenden Sie für interne Probleme das WDG Content Request Tool unter [http://aka.ms/pubrequest](http://aka.ms/pubrequest). 
