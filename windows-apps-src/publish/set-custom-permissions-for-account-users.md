---
author: jnHs
Description: Set roles or custom permissions for account users.
title: Legen Sie Rollen oder benutzerdefinierte Berechtigungen für Kontenbenutzer fest
ms.assetid: 99f3aa18-98b4-4919-bd7b-d78356b0bf78
ms.author: wdg-dev-content
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Benutzerrollen, Benutzerberechtigung, benutzerdefinierte Rollen, Zugriff für Benutzer, Berechtigungen anpassen, Standardrollen
ms.localizationpriority: high
ms.openlocfilehash: 3c62ff8a028af62512936e51bd81d3f3e229bd24
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="set-roles-or-custom-permissions-for-account-users"></a>Legen Sie Rollen oder benutzerdefinierte Berechtigungen für Kontenbenutzer fest

Wenn Sie [Ihrem Dev Center-Konto Benutzer hinzufügen](add-users-groups-and-azure-ad-applications.md) müssen Sie festlegen, welchen Zugriff Sie ihnen innerhalb des Kontos erlauben. Sie können ihnen [Standardrollen](#roles) zuweisen oder [die Berechtigungen so anpassen](#custom), dass die Benutzer über die entsprechende Zugriffsebene verfügen. Einige dieser benutzerdefinierten Berechtigungen gelten für das gesamte Konto, während andere für alle Produkte erteilt (oder auf bestimmte Produkte beschränkt) werden können.

> [!NOTE] 
> Unabhängig davon, ob Sie einen Benutzer, eine Gruppe oder eine Azure AD-Anwendung hinzufügen, können die gleichen Rollen und Berechtigungen übernommen werden.

Beim Ermitteln der Rollen oder Berechtigungen sollten Sie folgendes bedenken: 
-   Benutzer (einschließlich von Gruppen und Azure AD-Anwendungen) können mit den Berechtigungen für ihre jeweils zugewiesene Rolle auf das gesamte Dev Center-Konto zugreifen, es sei denn, Sie möchten die [Berechtigungen anpassen](#custom) und ihnen [Berechtigungen auf Produktebene](#product-level-permissions) erteilen, damit Sie nur mit spezifischen Apps und/oder Add-ons arbeiten können.
-   Sie können einem Benutzer, einer Gruppe oder einer Azure AD-Anwendung den Zugriff auf die Funktionen mehrerer Rollen gewähren, indem Sie mehrere Rollen auswählen oder indem Sie mithilfe benutzerdefinierter Berechtigungen den Zugriff gewähren, den Sie ihnen geben möchten.
-   Ein Benutzer mit einer bestimmten Rolle (oder einer Reihe benutzerdefinierter Berechtigungen) kann auch Teil einer Gruppe mit einer anderen Rolle (oder einem anderen Satz von Berechtigungen) sein. In diesem Fall hat der Benutzer Zugriff auf alle Funktionen, die mit der Gruppe und dem individuellen Konto verbunden sind.

> [!TIP]
> Dieses Thema gilt nur für das Entwicklerprogramm für Windows-Apps. Weitere Informationen zu Benutzerrollen im Hardware-Entwicklerprogramm finden Sie unter [Verwalten von Benutzerrolleng](https://docs.microsoft.com/windows-hardware/drivers/dashboard/managing-user-roles). Weitere Informationen zu Benutzerrollen im Windows-Desktopanwendungsprogramm finden Sie unter [Windows Desktopanwendungsprogramm](https://msdn.microsoft.com/library/windows/desktop/mt826504#users).


<span id="roles" />
## <a name="assign-roles-to-account-users"></a>Kontobenutzern Rollen zuweisen

Standardmäßig wird eine Reihe von standardmäßigen Rollen für die Auswhal angezeigt, wenn Sie Ihrem Dev Center-Konto einen Benutzer, Gruppen oder Azure AD-Anwendungen hinzufügen. Jede Rolle verfügt über spezifische Berechtigungen, mit denen bestimmte Funktionen innerhalb des Kontos ausgeführt werden können. 

Sofern Sie keine [benutzerdefinierten Berechtigungen](#custom) durch die Auswahl **benutzerdefinierten Berechtigungen** verwenden, müssen alle Benutzer, Gruppen oder Azure AD-Anwendungen, die Sie einem Konto hinzufügen, mindestens einer der folgenden Standardrollen zugewiesen sein. 

> [!NOTE]
> Der **Besitzer** des Kontos ist die Person, die es als erste mit einem Microsoft-Konto erstellt hat (und keiner der Benutzer, die über Azure AD hinzugefügt wurden). Dieser Kontobesitzer ist die einzige Person mit Vollzugriff auf das Konto. Hierzu zählt die Möglichkeit, Apps zu löschen, zu erstellen und zu bearbeiten, alle Kontobenutzer zu bearbeiten sowie sämtliche finanziellen Einstellungen und Kontoeinstellungen zu ändern. 


| Rolle                 | Beschreibung              |
|----------------------|--------------------------|
| Manager              | Verfügt über vollständigen Zugriff auf das Konto, kann jedoch keine Steuer- und Auszahlungseinstellungen ändern. Dies umfasst das Verwalten von Benutzern in Dev Center. Beachten Sie jedoch, dass die Fähigkeit zum Erstellen und Löschen von Benutzern im Azure AD-Mandanten von den Berechtigungen des Kontos in Azure AD abhängig ist. Das heißt, wenn einem Benutzer die Manager-Rolle zugewiesen ist, er jedoch nicht über globale Administratorberechtigungen im Azure AD der Organisation verfügt, kann er keine neuen Benutzer erstellen oder Benutzer aus dem Verzeichnis löschen (er kann jedoch die Dev Center-Rolle eines Benutzers ändern). <p> Hinweis: Wenn das Dev Center-Konto mit mehr als einem Azure AD-Mandanten verknüpft ist, kann der Manager nicht die vollständigen Details für einen Benutzer anzeigen (z.B. Vorname, Nachname, E-Mail-Kennwort-Wiederherstellung, und ob es sich um einen globalen Azure AD-Administrator handelt), es sei denn sie sind in dem gleichen Mandanten als der gleiche Benutzer mit einem Konto angemeldet, das über Berechtigungen als globaler Administrator für die Mandanten verfügt. Allerdings können sie Benutzer in jedem Mandanten hinzufügen und entfernen, die dem Dev Center-Konto zugeordnet sind. |
| Entwickler            | Kann Pakete hochladen und Apps und Add-Ons einreichen sowie den [Nutzungsbericht](usage-report.md) für Telemetriedetails einsehen. Kann keine finanziellen Informationen oder Kontoeinstellungen anzeigen.   |
| Mitwirkender im Geschäftsbereich | Kann [Integritäts](health-report.md)- und [Nutzungs](usage-report.md)-Berichte anzeigen. Kann keine Produkte erstellen oder übermitteln, Kontoeinstellungen ändern oder finanzielle Informationen anzeigen.                                         |
| Mitwirkender im Finanzbereich  | Kann [Auszahlungsberichte](payout-summary.md), finanzielle Informationen und Erwerbsberichte anzeigen. Kann keine Änderungen an Apps, Add-Ons oder Kontoeinstellungen vornehmen.                                                                                                                                   |
| Händler             | Kann auf [Kundenbewertungen reagieren](respond-to-customer-reviews.md) und nicht finanzbezogene [Analyseberichte](analytics.md) einsehen. Kann keine Änderungen an Apps, Add-Ons oder Kontoeinstellungen vornehmen.      |

In der nachfolgenden Tabelle sind einige der spezifischen Features aufgeführt, die für diese Rollen (und für den Kontobesitzer) verfügbar sind.

|                                 |    Kontobesitzer                 |    Manager                       |    Entwickler                     |    Mitwirkender im Geschäftsbereich    |    Mitwirkender im Finanzbereich    |    Händler                      |
|---------------------------------|----------------------------------|----------------------------------|----------------------------------|----------------------------|---------------------------|----------------------------------|
|    Erwerbsbericht           |    Kann anzeigen                      |    Kann anzeigen                      |     Kein Zugriff                    |     Kein Zugriff              |    Kann anzeigen               |    Kein Zugriff                     |
|    Feedbackbericht/Antworten    |    Kann Feedback anzeigen und senden    |    Kann Feedback anzeigen und senden    |    Kann Feedback anzeigen und senden    |     Kein Zugriff              |     Kein Zugriff             |    Kann Feedback anzeigen und senden    |
|    Integritätsbericht                |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                |     Kein Zugriff             |    Kein Zugriff                     |
|    Nutzungsbericht                 |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                      |    Kann anzeigen                |     Kein Zugriff             |    Kein Zugriff                     |
|    Auszahlungskonto               |    Kann aktualisieren                    |    Kein Zugriff                     |    Kein Zugriff                     |    Kein Zugriff               |    Kann anzeigen               |    Kein Zugriff                     |
|    Steuerprofil                  |    Kann aktualisieren                    |    Kein Zugriff                     |    Kein Zugriff                     |    Kein Zugriff               |    Kann anzeigen               |    Kein Zugriff                     |
|    Auszahlungsübersicht               |    Kann anzeigen                      |    Kein Zugriff                     |    Kein Zugriff                     |    Kein Zugriff               |    Kann anzeigen               |    Kein Zugriff                     |

Wenn keine der standardmäßigen Rollen geeignet ist oder wenn Sie den Zugriff auf bestimmte Apps und/oder Add-Ons einschränken möchten, können Sie benutzerdefinierte Berechtigungen für den Benutzer gewähren, indem Sie wie oben beschrieben **Berechtigungen anpassen** auswählen.


<span id="custom" />
## <a name="assign-custom-permissions-to-account-users"></a>Legen Sie benutzerdefinierte Berechtigungen für Kontenbenutzer fest

Um anstelle von Standardrollen benutzerdefinierte Berechtigungen zuzuordnen, klicken Sie beim Hinzufügen oder Bearbeiten des Benutzerkontos im Abschnitt **Rollen** auf **Berechtigungen anpassen**. 

Um eine Berechtigung für den Benutzer zu aktivieren, aktivieren Sie das Kontrollkästchen für die entsprechende Einstellung. 

![Anleitung für die Zugriffseinstellungen](images/permission_key.png)

- **Kein Zugriff**: Der Benutzer verfügt nicht über die angegebene Berechtigung.
- **Schreibgeschützt**: Der Benutzer kann Features im Zusammenhang mit dem angegebenen Bereich anzeigen, sie jedoch nicht ändern. 
- **Lese-/Schreibzugriff**: Der Benutzer kann für den Bereich Änderungen vornehmen sowie diesen anzeigen.
- **Gemischt**: Diese Option kann nicht direkt ausgewählt werden. **Gemischt** ist jedoch verfügbar, wenn Sie für die Berechtigung eine Zugriffskombination zugelassen haben. Wenn Sie z.B. **Schreibgeschützt** bei **Preise und Verfügbarkeit** für **Alle Produkte** festlegen, anschließend jedoch **Lese-/Schreibzugriff** auf **Preise und Verfügbarkeit** für ein bestimmtes Produkt gewähren, wird für **Preise und Verfügbarkeit** unter **Alle Produkte** „Gemischt“ angezeigt. Dasselbe gilt, wenn für einige Produkte als Berechtigung **Kein Zugriff** festgelegt ist, für andere jedoch **Lese-/Schreibzugriff** und/oder **Schreibgeschützt**.

Für einige Berechtigungen (z.B. im Zusammenhang mit dem Anzeigen von Analysedaten) kann nur Lesezugriff (**Schreibgeschützt**) gewährt werden. Beachten Sie, dass in der aktuellen Implementierung bei einigen Berechtigungen keine Unterscheidung zwischen **Schreibgeschützt** und **Lese-/Schreibzugriff** besteht. Ein besseres Verständnis der jeweiligen Funktionen, die mit **Schreibgeschützt** und/oder **Lese-/Schreibzugriff** gewährt werden, erhalten Sie anhand der Details zu den einzelnen Berechtigungen.

Die Details der einzelnen Berechtigungen werden in den folgenden Tabellen beschrieben.

## <a name="account-level-permissions"></a>Berechtigungen auf Kontoebene

Die Berechtigungen in diesem Abschnittkönnen nicht auf bestimmte Produkte beschränkt werden. Wird dem Benutzer Zugriff auf eine dieser Berechtigungen gewährt, gilt dies für das gesamte Konto.

<table>
    <colgroup>
    <col width="20%" />
    <col width="40%" />
    <col width="40%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Name der Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    </tr>
    </thead>
    <tbody>
<tr><td align="left">    **Kontoeinstellungen**                    </td><td align="left">  Kann alle Seiten im Abschnitt **Kontoeinstellungen** anzeigen, einschließlich der [Kontaktinformationen](managing-your-profile.md).       </td><td align="left">  Kann alle Seiten im Abschnitt **Kontoeinstellungen** anzeigen. Kann Änderungen an [Kontaktinformationen](managing-your-profile.md) und anderen Seiten, nicht jedoch am Auszahlungskonto oder Steuerprofil vornehmen (es sei denn, diese Berechtigung wird separat erteilt).            </td></tr>
<tr><td align="left">    **Kontenbenutzer**                       </td><td align="left">  Kann Benutzer anzeigen, die dem Konto im Abschnitt **Benutzer** hinzugefügt wurden.          </td><td align="left">  Kann dem Konto Benutzer hinzufügen und im Abschnitt **Benutzer** Änderungen an vorhandenen Benutzern vornehmen.             </td></tr>
<tr><td align="left">    **Bericht zur Anzeigenleistung auf Kontoebene** </td><td align="left">  Kann den [Bericht zur Anzeigenleistung auf Kontoebene](advertising-performance-report.md) anzeigen.      </td><td align="left">  n.a.   </td></tr>
<tr><td align="left">    **Anzeigenkampagnen**                        </td><td align="left">  Kann im Konto erstellte [Anzeigenkampagnen](create-an-ad-campaign-for-your-app.md) anzeigen.      </td><td align="left">  Kann im Konto erstellte [Anzeigenkampagnen](create-an-ad-campaign-for-your-app.md) erstellen, verwalten und anzeigen.          </td></tr>
<tr><td align="left">    **Anzeigenvermittlung**                        </td><td align="left">  Kann [Anzeigenvermittlungskonfigurationen](https://msdn.microsoft.com/library/windows/apps/xaml/mt149935.aspx) für alle Produkte des Kontos anzeigen.    </td><td align="left">  Kann [Anzeigenvermittlungskonfigurationen](https://msdn.microsoft.com/library/windows/apps/xaml/mt149935.aspx) für alle Produkte des Kontos anzeigen und ändern.        </td></tr>
<tr><td align="left">    **Berichte zur Anzeigenvermittlung**                </td><td align="left">  Kann den [Bericht zur Anzeigenvermittlung](ad-mediation-report.md) für alle Produkte des Kontos anzeigen.    </td><td align="left">  n.a.    </td></tr>
<tr><td align="left">    **Berichte zur Anzeigenleistung**              </td><td align="left">  Kann [Berichte zur Anzeigenleistung](advertising-performance-report.md) für alle Produkte des Kontos anzeigen.       </td><td align="left">  n.a.         </td></tr>
<tr><td align="left">    **Anzeigeneinheiten**                            </td><td align="left">  Kann die für das Konto erstellten [Anzeigeneinheiten](in-app-ads.md) anzeigen.    </td><td align="left">  Kann [Anzeigeneinheiten](in-app-ads.md) für das Konto erstellen, verwalten und anzeigen.             </td></tr>
<tr><td align="left">    **Partneranzeigen**                       </td><td align="left">  Kann die Nutzung von [Partneranzeigen](about-affiliate-ads.md) für alle Produkte des Kontos anzeigen.    </td><td align="left">  Kann die Nutzung von [Partneranzeigen](about-affiliate-ads.md) für alle Produkte des Kontos verwalten und anzeigen.                </td></tr>
<tr><td align="left">    **Berichte zur Partneranzeigenleistung**      </td><td align="left">  Kann den [Bericht zur Partneranzeigenleistung](affiliates-performance-report.md) für alle Produkte des Kontos anzeigen.   </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    **Berichte „Anzeigen für die App-Installation“**             </td><td align="left">  Können den [Bericht „Anzeigenkampagne“](promote-your-app-report.md) anzeigen.           </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    **Community-Anzeigen**                       </td><td align="left">  Kann die Nutzung kostenloser [Community-Anzeigen](about-community-ads.md) für alle Produkte des Kontos anzeigen.          </td><td align="left">  Kann die Nutzung kostenloser [Community-Anzeigen](about-community-ads.md) für alle Produkte des Kontos erstellen, verwalten und anzeigen.               </td></tr>
<tr><td align="left">    **Kontaktinformationen**                        </td><td align="left">  Kann [Kontaktinformationen](managing-your-profile.md) im Abschnitt mit den Kontoeinstellungen anzeigen.        </td><td align="left">  Kann [Kontaktinformationen](managing-your-profile.md) im Abschnitt mit den Kontoeinstellungen anzeigen und bearbeiten.            </td></tr>
<tr><td align="left">    **COPPA-Compliance**                    </td><td align="left">  Kann für alle Produkte des Kontos die Einstellungen für die [COPPA-Compliance](in-app-ads.md#coppa-compliance) anzeigen (die angeben, ob sich Produkte an Kinder unter 13Jahren richten).                                            </td><td align="left">  Kann für alle Produkte des Kontos die Einstellungen für die [COPPA-Compliance](in-app-ads.md#coppa-compliance) anzeigen und bearbeiten (die angeben, ob sich Produkte an Kinder unter 13Jahren richten).         </td></tr>
<tr><td align="left">    **Kundengruppen**                     </td><td align="left">  Kann [Kundengruppen](create-customer-groups.md) (Segmente und Flight-Gruppen) im Abschnitt **Kunden** anzeigen.      </td><td align="left">  Kann [Kundengruppen](create-customer-groups.md) (Segmente und Flight-Gruppen) im Abschnitt **Kunden** erstellen, bearbeiten und anzeigen.       </td></tr>
<tr><td align="left">    **Verwalten von Produktgruppen**&nbsp;\*                            </td><td align="left">  Kann die Seite zum Erstellen neuer Produktgruppen anzeigen, jedoch keine neuen Produktgruppen im Konto erstellen.    </td><td align="left">  Kann Produktgruppen erstellen und bearbeiten.     </td></tr>
<tr><td align="left">    **Neue Apps**                            </td><td align="left">  Kann die Seite zum Erstellen neuer Apps anzeigen, jedoch keine neuen Apps im Konto erstellen.    </td><td align="left">  Kann im Konto [neue Apps erstellen](create-your-app-by-reserving-a-name.md), indem neue App-Namen reserviert werden. Zudem können Übermittlungen erstellt und Apps an den Store übermittelt werden.     </td></tr>
<tr><td align="left">    **Neue Bündel**&nbsp;*                       </td><td align="left">  Kann die Seite zum Erstellen neuer Bündel anzeigen, jedoch keine neuen Bündel im Konto erstellen.     </td><td align="left">  Kann neue Produktbündel erstellen.          </td></tr>
<tr><td align="left">    **Partnerdienste**&nbsp;*                  </td><td align="left">  Kann Zertifikate für das Installieren in Diensten zum Abrufen von XTokens anzeigen.     </td><td align="left">  Kann Zertifikate für das Installieren in Diensten zum Abrufen von XTokens verwalten und anzeigen.       </td></tr>
<tr><td align="left">    **Auszahlungskonto**                      </td><td align="left">  Kann [Auszahlungskontodaten](setting-up-your-payout-account-and-tax-forms.md#payout-account) unter **Kontoeinstellungen** anzeigen.     </td><td align="left">  Kann [Auszahlungskontodaten](setting-up-your-payout-account-and-tax-forms.md#payout-account) unter **Kontoeinstellungen** bearbeiten und anzeigen.       </td></tr>
<tr><td align="left">    **Auszahlungsübersicht**                      </td><td align="left">  Kann die [Auszahlungsübersicht](payout-summary.md) anzeigen, um auf Auszahlungsberichtsdaten zuzugreifen und diese herunterzuladen.       </td><td align="left">  Kann die [Auszahlungsübersicht](payout-summary.md) anzeigen, um auf Auszahlungsberichtsdaten zuzugreifen und diese herunterzuladen.   </td></tr>
<tr><td align="left">    **Vertrauende Seiten**&nbsp;*                   </td><td align="left">  Kann vertrauende Seiten anzeigen, um XTokens abzurufen.    </td><td align="left">  Kann vertrauende Seiten verwalten und anzeigen, um XTokens abzurufen.     </td></tr>
<tr><td align="left">    **Anfordern von CDs**&nbsp;*                   </td><td align="left">  Können Spiele-CD-Anfragen sehen.    </td><td align="left">  Können Spiele-CD-Anfragen erstellen und sehen.     </td></tr>
<tr><td align="left">    **Sandboxes**&nbsp;*                         </td><td align="left">  Kann auf die Seite **Sandboxes** zugreifen und für das Konto die Sandboxes sowie alle gültigen Konfigurationen anzeigen. Kann nicht die Produkte und Übermittlungen für die jeweilige Sandbox anzeigen, sofern keine entsprechenden Berechtigungen auf Produktebene erteilt wurden. </td><td align="left">  Kann auf die Seite **Sandboxes** zugreifen und die Sandboxes im Konto anzeigen und verwalten, z.B. um Sandboxes zu erstellen und zu löschen oder deren Konfiguration zu verwalten. Kann nicht die Produkte und Übermittlungen für die jeweilige Sandbox anzeigen, sofern keine entsprechenden Berechtigungen auf Produktebene erteilt wurden.    </td></tr>
<tr><td align="left">    **Store-Verkaufsereignisse**&nbsp;\*                            </td><td align="left">  n.a.    </td><td align="left">  Kann die Option konfigurieren, automatisch Produkte im Store in Verkaufsereignisse aufzunehmen.     </td></tr>
<tr><td align="left">    **Steuerprofil**                         </td><td align="left">  Kann [Steuerprofildaten und -formulare](setting-up-your-payout-account-and-tax-forms.md#tax-forms) in den **Kontoeinstellungen** anzeigen.     </td><td align="left">  Kann Steuerformulare ausfüllen und [Steuerprofildaten](setting-up-your-payout-account-and-tax-forms.md#tax-forms) in den **Kontoeinstellungen** aktualisieren.     </td></tr>
<tr><td align="left">    **Testkonten**&nbsp;*                     </td><td align="left">  Kann Konten zum Testen der Xbox Live-Konfiguration anzeigen.      </td><td align="left">  Kann Konten zum Testen der Xbox Live-Konfiguration erstellen, verwalten und anzeigen.      </td></tr>
<tr><td align="left">    **Xbox-Geräte**                        </td><td align="left">  Kann im Abschnitt **Kontoeinstellungen** die für das Konto aktivierten Xbox-Entwicklungskonsolen anzeigen.       </td><td align="left">  Kann die für das Konto aktivierten Xbox-Entwicklungskonsolen im Abschnitt **Kontoeinstellungen** hinzufügen, entfernen und anzeigen.     </td></tr>
    </tbody>
    </table>

\ * Mit einem Sternchen (*) gekennzeichnete Berechtigungen gewähren Zugriff auf Features, die nicht für alle Konten verfügbar sind. Wenn Ihr Konto nicht für diese Features aktiviert wurde, ist Ihre Auswahl für diese Berechtigungen nicht wirksam.   


## <a name="product-level-permissions"></a>Berechtigungen auf Produktebene

Die Berechtigungen in diesem Abschnittkönnen für alle Produkte im Konto erteilt werden. Zudem können sie so angepasst werden, dass sie nur für ein oder mehrere bestimmte Produkte erteilt werden. 

Diese Berechtigungen auf Produktebene sind in vier Kategorien unterteilt: **Analysen**, **Monetarisierung**, **Veröffentlichung** und **Xbox Live**. Sie können die einzelnen Kategorien erweitern, um die jeweiligen Berechtigungen anzuzeigen. Sie haben auch die Option **Alle Berechtigungen** für einen oder mehrere bestimmte Produkte zu aktivieren.

Um eine Berechtigung für jedes Produkt des Kontos zu erteilen, treffen Sie in der Zeile **Alle Produkte** Ihre Auswahl für diese Berechtigung (indem Sie für das Feld **Schreibgeschützt** oder **Lese-/Schreibzugriff** aktivieren). 
 
> [!TIP]
> Die für **Alle Produkte** getroffene Auswahl gilt für sämtliche derzeit im Konto vorhandenen Produkte sowie für alle zukünftig für das Konto erstellten Produkte. Um zu verhindern, dass die Berechtigungen aus der Anwendung auf zukünftige Produkte zutreffen, wählen Sie sämtliche Produkte einzeln aus, anstatt **Alle Produkte** zu wählen.

Unterhalb der Zeile **Alle Produkte** sind die einzelnen Produkte des Kontos in jeweils eigenen Zeilen aufgeführt. Um nur für ein bestimmtes Produkt eine Berechtigung zu erteilen, treffen Sie Ihre Berechtigungsauswahl in der Zeile für das Produkt.

Jedes Add-On wird in einer separaten Zeile unterhalb des übergeordneten Produkts aufgeführt. Zudem gibt es die Zeile **Alle Add-Ons**. Die unter **Alle Add-Ons** getroffene Auswahl gilt für alle aktuellen Add-Ons des Produkts sowie für alle zukünftig für das Produkte erstellten Add-Ons.

Beachten Sie, dass einige Berechtigungen nicht für Add-Ons festgelegt werden können. Dies liegt entweder daran, dass sie nicht für Add-Ons gelten (z.B. die Berechtigung **Kundenfeedback**), oder dass die auf der Ebene des übergeordneten Produkts erteilte Berechtigung für alle Add-Ons des Produkts gilt (z.B. **Werbecodes**). Beachten Sie jedoch, dass alle für Add-Ons verfügbaren Berechtigungen separat festgelegt werden müssen. Add-Ons erben nicht die für das übergeordnete Produkt getroffene Auswahl. Wenn Sie z.B. einem Benutzer gestatten möchten, Preis- und Verfügbarkeitsoptionen für ein Add-On vorzunehmen, müssen Sie die Berechtigung **Preise und Verfügbarkeit** für das Add-On (oder für **Alle Add-Ons**) unabhängig davon aktivieren, ob Sie die Berechtigung **Preise und Verfügbarkeit** für das übergeordnete Produkt erteilt haben. 


### <a name="analytics"></a>Analysen

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **Käufe**     </td><td>    Kann die Berichte [Käufe](acquisitions-report.md) und [Add-On-Käufe](add-on-acquisitions-report.md) für das Produkt anzeigen.        </td><td>    Nicht verfügbar    </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt umfassen Berichte zu Add-On-Käufen)        </td><td>    Nicht verfügbar                         </td></tr>
    <tr><td align="left">    **Nutzung** </td><td>    Kann den [Bericht „Nutzung“](usage-report.md) für das Produkt anzeigen.     </td><td>    Nicht verfügbar       </td><td>    n.a.     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    **Integrität** </td><td>    Kann den [Bericht „Integrität“](health-report.md) für das Produkt anzeigen.    </td><td>    Nicht verfügbar     </td><td>    n.a.     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    **Kundenfeedback**    </td><td>    Kann die Berichte [Rezensionen](reviews-report.md) und [Feedback](feedback-report.md) für das Produkt anzeigen.       </td><td>    Nicht verfügbar (Um auf Feedback oder Rezensionen reagieren zu können, muss die Berechtigung **Kunden kontaktieren** erteilt werden)   </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    **Xbox-Analyse** </td><td>    Kann den Xbox-Analysebericht für das Produkt anzeigen. (Hinweis: Dieser Bericht ist noch nicht verfügbar.)    </td><td>    Nicht zutreffend   </td><td>    Nicht verfügbar       </td><td>    Nicht verfügbar          </td></tr>
    <tr><td align="left">    **Echtzeit**   </td><td>    Kann den Echtzeit-Bericht für das Produkt anzeigen. (Hinweis: Dieser Bericht ist zur Zeit nur über das [Dev Center-Insider-Programm](dev-center-insider-program.md) verfügbar.)      </td><td>    Nicht verfügbar   </td><td>    n.a.     </td><td>    Nicht verfügbar                 </td></tr>
    </tbody>
    </table>

### <a name="monetization"></a>Monetisierung

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **Werbecodes**     </td><td>    Kann Aufträge und Nutzungsdaten für [Werbecodes](generate-promotional-codes.md) für das Produkt und dessen Add-Ons anzeigen.         </td><td>    Kann Aufträge und Nutzungsdaten für [Werbecodes](generate-promotional-codes.md) für das Produkt und dessen Add-Ons anzeigen, verwalten und erstellen.          </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt gelten für alle Add-Ons)     </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt gelten für alle Add-Ons)     </td></tr>
    <tr><td align="left">    **Zielgerichtete Angebote**     </td><td>    Kann die [zielgerichteten Angebote](use-targeted-offers-to-maximize-engagement-and-conversions.md) für das Produkt sehen.         </td><td>    Kann [zielgerichtete Angebote](use-targeted-offers-to-maximize-engagement-and-conversions.md) für das Produkt erstellen, verwalten und anzeigen.          </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar      </td></tr>
    <tr><td align="left">    **Kunden kontaktieren**  </td><td>    Kann [Reaktionen auf Kundenfeedback](respond-to-customer-feedback.md) und [Antworten auf Kundenrezensionen](respond-to-customer-reviews.md) anzeigen, sofern zudem die Berechtigung **Kundenfeedback** erteilt wurde. Kann zudem für das Produkt erstellte [benutzerorientierte Benachrichtigungen](send-push-notifications-to-your-apps-customers.md) anzeigen.    </td><td>    Kann [auf Kundenfeedback reagieren](respond-to-customer-feedback.md) und [auf Kundenrezensionen antworten](respond-to-customer-reviews.md), sofern die Berechtigung **Kundenfeedback** ebenfalls erteilt wurde. Kann zudem für das Produkt [benutzerorientierte Benachrichtigungen erstellen und senden](send-push-notifications-to-your-apps-customers.md).                   </td><td>    Nicht verfügbar         </td><td>    Nicht verfügbar                          </td></tr>
    <tr><td align="left">    **Experimentation**</td><td>    Kann [Experimente (A/B-Tests)](../monetize/run-app-experiments-with-a-b-testing.md) sowie Experimentdaten für das Produkt anzeigen.   </td><td>    Kann [Experimente (A/B-Tests)](../monetize/run-app-experiments-with-a-b-testing.md) für das Produkt erstellen, verwalten und anzeigen sowie Experimentdaten anzeigen.     </td><td>    Nicht verfügbar  </td><td>    n.a.                 </td></tr>
    <tr><td align="left">    **Store-Verkaufsereignisse**&nbsp;\*</td><td>    Kann den Verkaufsereignisstatus für das Produkt anzeigen.   </td><td>    Kann das Produkt zu Verkaufsereignissen hinzufügen und Rabatte konfigurieren.      </td><td>    Kann den Verkaufsereignisstatus für das Produkt anzeigen.   </td><td>    Kann das Produkt zu Verkaufsereignissen hinzufügen und Rabatte konfigurieren.      </td></tr>

    </tbody>
    </table>

### <a name="publishing"></a>Veröffentlichung 

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **Preise und Verfügbarkeit**  </td><td>    Kann die Seite [Preise und Verfügbarkeit](set-app-pricing-and-availability.md) von Produktübermittlungen anzeigen.     </td><td>    Kann die Seite [Preise und Verfügbarkeit](set-app-pricing-and-availability.md) von Produktübermittlungen anzeigen und bearbeiten. </td><td>    Kann die Seite [Preise und Verfügbarkeit](set-add-on-pricing-and-availability.md) von Add-On-Übermittlungen anzeigen.   </td><td>    Kann die Seite [Preise und Verfügbarkeit](set-add-on-pricing-and-availability.md) von Add-On-Übermittlungen anzeigen und bearbeiten.          </td></tr>
    <tr><td align="left">    **Eigenschaften**   </td><td>    Kann die Seite [Eigenschaften](enter-app-properties.md) von Produktübermittlungen anzeigen.      </td><td>    Kann die Seite [Eigenschaften](enter-app-properties.md) von Produktübermittlungen anzeigen und bearbeiten.       </td><td>    Kann die Seite [Eigenschaften](enter-add-on-properties.md) von Add-On-Übermittlungen anzeigen.     </td><td>    Kann die Seite [Eigenschaften](enter-add-on-properties.md) von Add-On-Übermittlungen anzeigen und bearbeiten.               </td></tr>
    <tr><td align="left">    **Altersfreigaben**    </td><td>    Kann die Seite [Altersfreigaben](age-ratings.md) von Produktübermittlungen anzeigen.       </td><td>    Kann die Seite [Altersfreigaben](age-ratings.md) von Produktübermittlungen anzeigen und bearbeiten.    </td><td>    * Kann die Seite „Altersfreigaben“ von Add-On-Übermittlungen anzeigen.          </td><td>    * Kann die Seite „Altersfreigaben“ von Add-On-Übermittlungen anzeigen und bearbeiten.       </td></tr>
    <tr><td align="left">    **Pakete**        </td><td>    Kann die Seite [Pakete](upload-app-packages.md) für Produktübermittlungen anzeigen.  </td><td>    Kann die Seite [Pakete](upload-app-packages.md) für Produktübermittlungen anzeigen und bearbeiten sowie Pakete hochladen.     </td><td>    * Kann die Gerätefamilienausrichtung und -pakete (sofern zutreffend) für Add-On-Übermittlungen anzeigen.   </td><td>    * Kann die Gerätefamilienausrichtung für Add-On-Übermittlungen anzeigen und bearbeiten sowie ggf. Pakete hochladen.             </td></tr>
    <tr><td align="left">    **Store-Einträge**  </td><td>    Kann die [Store-Eintragsseite(n)](create-app-store-listings.md) für Produktübermittlungen anzeigen.  </td><td>    Kann die [Seite(n) mit Store-Einträgen](create-app-store-listings.md) für Produktübermittlungen anzeigen und bearbeiten sowie neue Store-Einträge für verschiedene Sprachen hinzufügen.     </td><td>    Kann die [Seite(n) mit Store-Einträgen](create-add-on-store-listings.md) für Add-On-Übermittlungen anzeigen.            </td><td>    Kann die [Seite(n) mit Store-Einträgen](create-add-on-store-listings.md) für Add-On-Übermittlungen anzeigen und bearbeiten sowie neue Store-Einträge für verschiedene Sprachen hinzufügen.                 </td></tr>
    <tr><td align="left">    **Store-Übermittlung**     </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.           </td><td>    Kann das Produkt an den Store übermitteln und Zertifizierungsberichte anzeigen. Dies gilt sowohl für neue als auch für aktualisierte Übermittlungen. </td><td>Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.     </td><td>    Kann das Add-On an den Store übermitteln und Zertifizierungsberichte anzeigen. Dies gilt sowohl für neue als auch für aktualisierte Übermittlungen.</td></tr>
    <tr><td align="left">    **Erstellen von neuen Übermittlungen**       </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.        </td><td>    Kann neue [Übermittlungen](app-submissions.md) für das Produkt erstellen.  </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.   </td><td>    Kann neue [Übermittlungen](add-on-submissions.md) für das Add-On erstellen.        </td></tr>
    <tr><td align="left">    **Neue Add-Ons**    </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist. </td><td>    Kann neue [Add-Ons](set-your-add-on-product-id.md) für das Produkt erstellen. </td><td>    Nicht verfügbar    </td><td>    Nicht verfügbar        </td></tr>
    <tr><td align="left">    **Namensreservierungen**   </td><td>    Kann die Seite [App-Namen verwalten](manage-app-names.md) für das Produkt anzeigen.</td><td>    Kann die Seite [App-Namen verwalten](manage-app-names.md) für das Produkt anzeigen und bearbeiten sowie zusätzliche Namen reservieren und reservierte Namen löschen. </td><td>   * Kann reservierte Namen für das Add-On anzeigen.    </td><td>   * Kann reservierte Namen für das Add-On anzeigen und bearbeiten.          </td></tr>
    </tbody>
    </table>

### <a name="xbox-live-"></a>Xbox Live \*

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **App-Kanäle**&nbsp;\*</td><td>    n.a.  </td><td>    Kann Werbevideokanäle auf der Xbox-Konsole für die Anzeige über OneGuide veröffentlichen.  </td><td>  Nicht verfügbar </td><td> n.a. </td></tr>
    <tr><td align="left">    **Dienstkonfiguration**&nbsp;\*    </td><td>    Kann Einstellungen für Erfolge, Multiplayer, Bestenlisten und weitere Xbox Live-Konfigurationsoptionen für das Produkt anzeigen.  </td><td>    Kann Einstellungen für Erfolge, Multiplayer, Bestenlisten und weitere Xbox Live-Konfigurationsoptionen für das Produkt anzeigen und bearbeiten.  </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar                      </td></tr>
</tbody>
</table>

\ * Mit einem Sternchen (*) gekennzeichnete Berechtigungen gewähren Zugriff auf Features, die nicht für alle Konten verfügbar sind. Wenn Ihr Konto nicht für diese Features aktiviert wurde, ist Ihre Auswahl für diese Berechtigungen nicht wirksam.  
