---
author: jnHs
Description: Set roles or custom permissions for account users.
title: Legen Sie Rollen oder benutzerdefinierte Berechtigungen für Kontenbenutzer fest
ms.assetid: 99f3aa18-98b4-4919-bd7b-d78356b0bf78
ms.author: wdg-dev-content
ms.date: 07/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Benutzerrollen, Benutzerberechtigung, benutzerdefinierte Rollen, Zugriff für Benutzer, Berechtigungen anpassen, Standardrollen
ms.localizationpriority: medium
ms.openlocfilehash: a4100248857af655f388ad318bb3ae5176aaf046
ms.sourcegitcommit: c8f6866100a4b38fdda8394ea185b02d7af66411
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "3956554"
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
> Dieses Thema gilt nur für das Entwicklerprogramm für Windows-Apps. Weitere Informationen zu Benutzerrollen im Hardware-Entwicklerprogramm finden Sie unter [Verwalten von Benutzerrolleng](https://docs.microsoft.com/windows-hardware/drivers/dashboard/managing-user-roles). Weitere Informationen zu Benutzerrollen im Windows-Desktopanwendungsprogramm finden Sie unter [Windows Desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#add-and-manage-account-users).


<span id="roles" />

## <a name="assign-roles-to-account-users"></a>Kontobenutzern Rollen zuweisen

Standardmäßig wird eine Reihe von standardmäßigen Rollen für die Auswhal angezeigt, wenn Sie Ihrem Dev Center-Konto einen Benutzer, Gruppen oder Azure AD-Anwendungen hinzufügen. Jede Rolle verfügt über spezifische Berechtigungen, mit denen bestimmte Funktionen innerhalb des Kontos ausgeführt werden können. 

Sofern Sie keine [benutzerdefinierten Berechtigungen](#custom) durch die Auswahl **benutzerdefinierten Berechtigungen** verwenden, müssen alle Benutzer, Gruppen oder Azure AD-Anwendungen, die Sie einem Konto hinzufügen, mindestens einer der folgenden Standardrollen zugewiesen sein. 

> [!NOTE]
> Der **Besitzer** des Kontos ist die Person, die es als erste mit einem Microsoft-Konto erstellt hat (und keiner der Benutzer, die über Azure AD hinzugefügt wurden). Dieser Kontobesitzer ist die einzige Person mit Vollzugriff auf das Konto. Hierzu zählt die Möglichkeit, Apps zu löschen, zu erstellen und zu bearbeiten, alle Kontobenutzer zu bearbeiten sowie sämtliche finanziellen Einstellungen und Kontoeinstellungen zu ändern. 


| Rolle                 | Beschreibung              |
|----------------------|--------------------------|
| Manager              | Verfügt über vollständigen Zugriff auf das Konto, kann jedoch keine Steuer- und Auszahlungseinstellungen ändern. Dies umfasst das Verwalten von Benutzern in Dev Center. Beachten Sie jedoch, dass die Fähigkeit zum Erstellen und Löschen von Benutzern im Azure AD-Mandanten von den Berechtigungen des Kontos in Azure AD abhängig ist. Das heißt, wenn einem Benutzer die Manager-Rolle zugewiesen ist, er jedoch nicht über globale Administratorberechtigungen im Azure AD der Organisation verfügt, kann er keine neuen Benutzer erstellen oder Benutzer aus dem Verzeichnis löschen (er kann jedoch die Dev Center-Rolle eines Benutzers ändern). <p> Hinweis: Wenn das Dev Center-Konto mit mehr als einem Azure AD-Mandanten verknüpft ist, kann der Manager nicht die vollständigen Details für einen Benutzer anzeigen (z.B. Vorname, Nachname, E-Mail-Kennwort-Wiederherstellung, und ob es sich um einen globalen Azure AD-Administrator handelt), es sei denn sie sind in dem gleichen Mandanten als der gleiche Benutzer mit einem Konto angemeldet, das über Berechtigungen als globaler Administrator für die Mandanten verfügt. Allerdings können sie Benutzer in jedem Mandanten hinzufügen und entfernen, die dem Dev Center-Konto zugeordnet sind. |
| Entwickler            | Kann Pakete hochladen und Apps und Add-Ons einreichen sowie den [Nutzungsbericht](usage-report.md) für Telemetriedetails einsehen. Können [Geräteübergreifende Benutzeroberflächen](https://go.microsoft.com/fwlink/?linkid=874042) -Funktionen zugreifen. Kann keine finanziellen Informationen oder Kontoeinstellungen anzeigen.   |
| Mitwirkender im Geschäftsbereich | Kann [Integritäts](health-report.md)- und [Nutzungs](usage-report.md)-Berichte anzeigen. Kann keine Produkte erstellen oder übermitteln, Kontoeinstellungen ändern oder finanzielle Informationen anzeigen.   |
| Mitwirkender im Finanzbereich  | Kann [Auszahlungsberichte](payout-summary.md), finanzielle Informationen und Erwerbsberichte anzeigen. Kann keine Änderungen an Apps, Add-Ons oder Kontoeinstellungen vornehmen.    |
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
<tr><td align="left">    <b>Kontoeinstellungen</b>                    </td><td align="left">  Kann alle Seiten im Abschnitt <b>Kontoeinstellungen</b> anzeigen, einschließlich der <a href="managing-your-profile.md">Kontaktinformationen</a>.       </td><td align="left">  Kann alle Seiten im Abschnitt <b>Kontoeinstellungen</b> anzeigen. Kann Änderungen an <a href="managing-your-profile.md">Kontaktinformationen</a> und anderen Seiten, nicht jedoch am Auszahlungskonto oder Steuerprofil vornehmen (es sei denn, diese Berechtigung wird separat erteilt).            </td></tr>
<tr><td align="left">    <b>Kontenbenutzer</b>                       </td><td align="left">  Kann Benutzer anzeigen, die dem Konto im Abschnitt <b>Benutzer</b> hinzugefügt wurden.          </td><td align="left">  Kann dem Konto Benutzer hinzufügen und im Abschnitt <b>Benutzer</b> Änderungen an vorhandenen Benutzern vornehmen.             </td></tr>
<tr><td align="left">    <b>Bericht zur Anzeigenleistung auf Kontoebene</b> </td><td align="left">  Kann den <a href="advertising-performance-report.md">Bericht zur Anzeigenleistung auf Kontoebene</a> anzeigen.      </td><td align="left">  n.a.   </td></tr>
<tr><td align="left">    <b>Anzeigenkampagnen</b>                        </td><td align="left">  Kann im Konto erstellte <a href="create-an-ad-campaign-for-your-app.md">Anzeigenkampagnen</a> anzeigen.      </td><td align="left">  Kann im Konto erstellte <a href="create-an-ad-campaign-for-your-app.md">Anzeigenkampagnen</a> erstellen, verwalten und anzeigen.          </td></tr>
<tr><td align="left">    <b>Anzeigenvermittlung</b>                        </td><td align="left">  Kann Anzeigenvermittlungskonfigurationen für alle Produkte des Kontos anzeigen.    </td><td align="left">  Kann Anzeigenvermittlungskonfigurationen für alle Produkte des Kontos anzeigen und ändern.        </td></tr>
<tr><td align="left">    <b>Berichte zur Anzeigenvermittlung</b>                </td><td align="left">  Kann den <a href="ad-mediation-report.md">Bericht zur Anzeigenvermittlung</a> für alle Produkte des Kontos anzeigen.    </td><td align="left">  n.a.    </td></tr>
<tr><td align="left">    <b>Berichte zur Anzeigenleistung</b>              </td><td align="left">  Kann <a href="advertising-performance-report.md">Berichte zur Anzeigenleistung</a> für alle Produkte des Kontos anzeigen.       </td><td align="left">  n.a.         </td></tr>
<tr><td align="left">    <b>Anzeigeneinheiten</b>                            </td><td align="left">  Kann die für das Konto erstellten <a href="in-app-ads.md">Anzeigeneinheiten</a> anzeigen.    </td><td align="left">  Kann <a href="in-app-ads.md">Anzeigeneinheiten</a> für das Konto erstellen, verwalten und anzeigen.             </td></tr>
<tr><td align="left">    <b>Partneranzeigen</b>                       </td><td align="left">  Kann die Nutzung von <a href="about-affiliate-ads.md">Partneranzeigen</a> für alle Produkte des Kontos anzeigen.    </td><td align="left">  Kann die Nutzung von <a href="about-affiliate-ads.md">Partneranzeigen</a> für alle Produkte des Kontos verwalten und anzeigen.                </td></tr>
<tr><td align="left">    <b>Berichte zur Partneranzeigenleistung</b>      </td><td align="left">  Kann den <a href="affiliates-performance-report.md">Bericht zur Partneranzeigenleistung</a> für alle Produkte des Kontos anzeigen.   </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    <b>Berichte „Anzeigen für die App-Installation“</b>             </td><td align="left">  Können den <a href="promote-your-app-report.md">Bericht „Anzeigenkampagne“</a> anzeigen.           </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    <b>Community-Anzeigen</b>                       </td><td align="left">  Kann die Nutzung kostenloser <a href="about-community-ads.md">Community-Anzeigen</a> für alle Produkte des Kontos anzeigen.          </td><td align="left">  Kann die Nutzung kostenloser <a href="about-community-ads.md">Community-Anzeigen</a> für alle Produkte des Kontos erstellen, verwalten und anzeigen.               </td></tr>
<tr><td align="left">    <b>Kontaktinformationen</b>                        </td><td align="left">  Kann <a href="managing-your-profile.md">Kontaktinformationen</a> im Abschnitt mit den Kontoeinstellungen anzeigen.        </td><td align="left">  Kann <a href="managing-your-profile.md">Kontaktinformationen</a> im Abschnitt mit den Kontoeinstellungen anzeigen und bearbeiten.            </td></tr>
<tr><td align="left">    <b>COPPA-Compliance</b>                    </td><td align="left">  Kann für alle Produkte des Kontos die Einstellungen für die <a href="in-app-ads.md#coppa-compliance">COPPA-Compliance</a> anzeigen (die angeben, ob sich Produkte an Kinder unter 13Jahren richten).                                            </td><td align="left">  Kann für alle Produkte des Kontos die Einstellungen für die <a href="in-app-ads.md#coppa-compliance">COPPA-Compliance</a> anzeigen und bearbeiten (die angeben, ob sich Produkte an Kinder unter 13Jahren richten).         </td></tr>
<tr><td align="left">    <b>Kundengruppen</b>                     </td><td align="left">  <a href="create-customer-groups.md">Kundengruppen</a> (Segmente und bekannte Benutzergruppen) können angezeigt werden.      </td><td align="left">  Können erstellen, bearbeiten und Anzeigen von <a href="create-customer-groups.md">Kundengruppen</a> (Segmente und bekannte Benutzergruppen).       </td></tr>
<tr><td align="left">    <b>Verwalten von Produktgruppen</b>&nbsp;*                            </td><td align="left">  Kann die Seite zum Erstellen neuer Produktgruppen anzeigen, jedoch keine neuen Produktgruppen im Konto erstellen.    </td><td align="left">  Kann Produktgruppen erstellen und bearbeiten.     </td></tr>
<tr><td align="left">    <b>Neue Apps</b>                            </td><td align="left">  Kann die Seite zum Erstellen neuer Apps anzeigen, jedoch keine neuen Apps im Konto erstellen.    </td><td align="left">  Kann im Konto <a href="create-your-app-by-reserving-a-name.md">neue Apps erstellen</a>, indem neue App-Namen reserviert werden. Zudem können Übermittlungen erstellt und Apps an den Store übermittelt werden.     </td></tr>
<tr><td align="left">    <b>Neue Bündel</b>&nbsp;*                       </td><td align="left">  Kann die Seite zum Erstellen neuer Bündel anzeigen, jedoch keine neuen Bündel im Konto erstellen.     </td><td align="left">  Kann neue Produktbündel erstellen.          </td></tr>
<tr><td align="left">    <b>Partnerdienste</b>&nbsp;*                  </td><td align="left">  Kann Zertifikate für das Installieren in Diensten zum Abrufen von XTokens anzeigen.     </td><td align="left">  Kann Zertifikate für das Installieren in Diensten zum Abrufen von XTokens verwalten und anzeigen.       </td></tr>
<tr><td align="left">    <b>Auszahlungskonto</b>                      </td><td align="left">  Kann <a href="setting-up-your-payout-account-and-tax-forms.md#payout-account">Auszahlungskontodaten</a> unter <b>Kontoeinstellungen</b> anzeigen.     </td><td align="left">  Kann <a href="setting-up-your-payout-account-and-tax-forms.md#payout-account">Auszahlungskontodaten</a> unter <b>Kontoeinstellungen</b> bearbeiten und anzeigen.       </td></tr>
<tr><td align="left">    <b>Auszahlungsübersicht</b>                      </td><td align="left">  Kann die <a href="payout-summary.md">Auszahlungsübersicht</a> anzeigen, um auf Auszahlungsberichtsdaten zuzugreifen und diese herunterzuladen.       </td><td align="left">  Kann die <a href="payout-summary.md">Auszahlungsübersicht</a> anzeigen, um auf Auszahlungsberichtsdaten zuzugreifen und diese herunterzuladen.   </td></tr>
<tr><td align="left">    <b>Vertrauende Seiten</b>&nbsp;*                   </td><td align="left">  Kann vertrauende Seiten anzeigen, um XTokens abzurufen.    </td><td align="left">  Kann vertrauende Seiten verwalten und anzeigen, um XTokens abzurufen.     </td></tr>
<tr><td align="left">    <b>Anfordern von CDs</b>&nbsp;*                   </td><td align="left">  Können Spiele-CD-Anfragen sehen.    </td><td align="left">  Können Spiele-CD-Anfragen erstellen und sehen.     </td></tr>
<tr><td align="left">    <b>Sandboxes</b>&nbsp;*                         </td><td align="left">  Kann auf die Seite <b>Sandboxes</b> zugreifen und für das Konto die Sandboxes sowie alle gültigen Konfigurationen anzeigen. Kann nicht die Produkte und Übermittlungen für die jeweilige Sandbox anzeigen, sofern keine entsprechenden Berechtigungen auf Produktebene erteilt wurden. </td><td align="left">  Kann auf die Seite <b>Sandboxes</b> zugreifen und die Sandboxes im Konto anzeigen und verwalten, z.B. um Sandboxes zu erstellen und zu löschen oder deren Konfiguration zu verwalten. Kann nicht die Produkte und Übermittlungen für die jeweilige Sandbox anzeigen, sofern keine entsprechenden Berechtigungen auf Produktebene erteilt wurden.    </td></tr>
<tr><td align="left">    <b>Store-Verkaufsereignisse</b>&nbsp;*                            </td><td align="left">  n.a.    </td><td align="left">  Kann die Option konfigurieren, automatisch Produkte im Store in Verkaufsereignisse aufzunehmen.     </td></tr>
<tr><td align="left">    <b>Steuerprofil</b>                         </td><td align="left">  Kann <a href="setting-up-your-payout-account-and-tax-forms.md#tax-forms">Steuerprofildaten und -formulare</a> in den <b>Kontoeinstellungen</b> anzeigen.     </td><td align="left">  Kann Steuerformulare ausfüllen und <a href="setting-up-your-payout-account-and-tax-forms.md#tax-forms">Steuerprofildaten</a> in den <b>Kontoeinstellungen</b> aktualisieren.     </td></tr>
<tr><td align="left">    <b>Testkonten</b>&nbsp;*                     </td><td align="left">  Kann Konten zum Testen der Xbox Live-Konfiguration anzeigen.      </td><td align="left">  Kann Konten zum Testen der Xbox Live-Konfiguration erstellen, verwalten und anzeigen.      </td></tr>
<tr><td align="left">    <b>Xbox-Geräte</b>                        </td><td align="left">  Kann im Abschnitt <b>Kontoeinstellungen</b> die für das Konto aktivierten Xbox-Entwicklungskonsolen anzeigen.       </td><td align="left">  Kann die für das Konto aktivierten Xbox-Entwicklungskonsolen im Abschnitt <b>Kontoeinstellungen</b> hinzufügen, entfernen und anzeigen.     </td></tr>
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
    <tr><td align="left">    <b>Käufe</b>     </td><td>    Kann die Berichte <a href="acquisitions-report.md">Käufe</a> und <a href="add-on-acquisitions-report.md">Add-On-Käufe</a> für das Produkt anzeigen.        </td><td>    Nicht verfügbar    </td><td>    N/v (Einstellungen für das übergeordnete Produkt umfassen den Bericht **Add-on-Käufe** )        </td><td>    Nicht verfügbar                         </td></tr>
    <tr><td align="left">    <b>Nutzung</b> </td><td>    Kann den <a href="usage-report.md">Bericht „Nutzung“</a> für das Produkt anzeigen.     </td><td>    Nicht verfügbar       </td><td>    n.a.     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    <b>Integrität</b> </td><td>    Kann den <a href="health-report.md">Bericht „Integrität“</a> für das Produkt anzeigen.    </td><td>    Nicht verfügbar     </td><td>    n.a.     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    <b>Kundenfeedback</b>    </td><td>    Kann die Berichte <a href="reviews-report.md">Rezensionen</a> und <a href="feedback-report.md">Feedback</a> für das Produkt anzeigen.       </td><td>    Nicht verfügbar (Um auf Feedback oder Rezensionen reagieren zu können, muss die Berechtigung <b>Kunden kontaktieren</b> erteilt werden)   </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    <b>Xbox-Analyse</b> </td><td>    Können die [Xbox-Analysebericht](xbox-analytics-report.md) für das Produkt anzeigen.    </td><td>    n.a.   </td><td>    n.a.       </td><td>    Nicht verfügbar          </td></tr>
    <tr><td align="left">    <b>Echtzeit</b>   </td><td>    Kann den Echtzeit-Bericht für das Produkt anzeigen. (Hinweis: Dieser Bericht ist zur Zeit nur über das <a href="dev-center-insider-program.md">Dev Center-Insider-Programm</a> verfügbar.)      </td><td>    Nicht verfügbar   </td><td>    n.a.     </td><td>    Nicht verfügbar                 </td></tr>
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
    <tr><td align="left">    <b>Werbecodes</b>     </td><td>    Kann Aufträge und Nutzungsdaten für <a href="generate-promotional-codes.md">Werbecodes</a> für das Produkt und dessen Add-Ons anzeigen.         </td><td>    Kann Aufträge und Nutzungsdaten für <a href="generate-promotional-codes.md">Werbecodes</a> für das Produkt und dessen Add-Ons anzeigen, verwalten und erstellen.          </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt gelten für alle Add-Ons)     </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt gelten für alle Add-Ons)     </td></tr>
    <tr><td align="left">    <b>Zielgerichtete Angebote</b>     </td><td>    Kann die <a href="use-targeted-offers-to-maximize-engagement-and-conversions.md">zielgerichteten Angebote</a> für das Produkt sehen.         </td><td>    Kann <a href="use-targeted-offers-to-maximize-engagement-and-conversions.md">zielgerichtete Angebote</a> für das Produkt erstellen, verwalten und anzeigen.          </td><td>    n.a.     </td><td>    n.a.      </td></tr>
    <tr><td align="left">    <b>Kunden kontaktieren</b>  </td><td>    Kann <a href="respond-to-customer-feedback.md">Reaktionen auf Kundenfeedback</a> und <a href="respond-to-customer-reviews.md">Antworten auf Kundenrezensionen</a> anzeigen, sofern zudem die Berechtigung <b>Kundenfeedback</b> erteilt wurde. Kann zudem für das Produkt erstellte <a href="send-push-notifications-to-your-apps-customers.md">benutzerorientierte Benachrichtigungen</a> anzeigen.    </td><td>    Können Sie <a href="respond-to-customer-feedback.md">auf Kundenfeedback reagieren</a> und <a href="respond-to-customer-reviews.md">Reagieren auf kundenrezensionen</a>, solange die <b>Kundenfeedback</b> Berechtigung ebenfalls erteilt wurde. Kann zudem für das Produkt <a href="send-push-notifications-to-your-apps-customers.md">benutzerorientierte Benachrichtigungen erstellen und senden</a>.                   </td><td>    Nicht verfügbar         </td><td>    Nicht verfügbar                          </td></tr>
    <tr><td align="left">    <b>Experimentation</b></td><td>    Kann <a href="../monetize/run-app-experiments-with-a-b-testing.md">Experimente (A/B-Tests)</a> sowie Experimentdaten für das Produkt anzeigen.   </td><td>    Kann <a href="../monetize/run-app-experiments-with-a-b-testing.md">Experimente (A/B-Tests)</a> für das Produkt erstellen, verwalten und anzeigen sowie Experimentdaten anzeigen.     </td><td>    Nicht verfügbar  </td><td>    n.a.                 </td></tr>
    <tr><td align="left">    <b>Store-Verkaufsereignisse</b>&nbsp;*</td><td>    Kann den Verkaufsereignisstatus für das Produkt anzeigen.   </td><td>    Kann das Produkt zu Verkaufsereignissen hinzufügen und Rabatte konfigurieren.      </td><td>    Kann den Verkaufsereignisstatus für das Produkt anzeigen.   </td><td>    Kann das Produkt zu Verkaufsereignissen hinzufügen und Rabatte konfigurieren.      </td></tr>
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
    <tr><td align="left">    <b>Preise und Verfügbarkeit</b>  </td><td>    Kann die Seite <a href="set-app-pricing-and-availability.md">Preise und Verfügbarkeit</a> von Produktübermittlungen anzeigen.     </td><td>    Kann die Seite <a href="set-app-pricing-and-availability.md">Preise und Verfügbarkeit</a> von Produktübermittlungen anzeigen und bearbeiten. </td><td>    Kann die Seite <a href="set-add-on-pricing-and-availability.md">Preise und Verfügbarkeit</a> von Add-On-Übermittlungen anzeigen.   </td><td>    Kann die Seite <a href="set-add-on-pricing-and-availability.md">Preise und Verfügbarkeit</a> von Add-On-Übermittlungen anzeigen und bearbeiten.          </td></tr>
    <tr><td align="left">    <b>Eigenschaften</b>   </td><td>    Kann die Seite <a href="enter-app-properties.md">Eigenschaften</a> von Produktübermittlungen anzeigen.      </td><td>    Kann die Seite <a href="enter-app-properties.md">Eigenschaften</a> von Produktübermittlungen anzeigen und bearbeiten.       </td><td>    Kann die Seite <a href="enter-add-on-properties.md">Eigenschaften</a> von Add-On-Übermittlungen anzeigen.     </td><td>    Kann die Seite <a href="enter-add-on-properties.md">Eigenschaften</a> von Add-On-Übermittlungen anzeigen und bearbeiten.               </td></tr>
    <tr><td align="left">    <b>Altersfreigaben</b>    </td><td>    Kann die Seite <a href="age-ratings.md">Altersfreigaben</a> von Produktübermittlungen anzeigen.       </td><td>    Kann die Seite <a href="age-ratings.md">Altersfreigaben</a> von Produktübermittlungen anzeigen und bearbeiten.    </td><td>    Kann die Seite „Altersfreigaben“ von Add-On-Übermittlungen anzeigen.          </td><td>     Kann die Seite „Altersfreigaben“ von Add-On-Übermittlungen anzeigen und bearbeiten.       </td></tr>
    <tr><td align="left">    <b>Pakete</b>        </td><td>    Kann die Seite <a href="upload-app-packages.md">Pakete</a> für Produktübermittlungen anzeigen.  </td><td>    Kann die Seite <a href="upload-app-packages.md">Pakete</a> für Produktübermittlungen anzeigen und bearbeiten sowie Pakete hochladen.     </td><td>   Kann die Gerätefamilienausrichtung und -pakete (sofern zutreffend) für Add-On-Übermittlungen anzeigen.   </td><td>     Kann die Gerätefamilienausrichtung für Add-On-Übermittlungen anzeigen und bearbeiten sowie ggf. Pakete hochladen.             </td></tr>
    <tr><td align="left">    <b>Store-Einträge</b>  </td><td>    Kann die <a href="create-app-store-listings.md">Store-Eintragsseite(n)</a> für Produktübermittlungen anzeigen.  </td><td>    Kann die <a href="create-app-store-listings.md">Seite(n) mit Store-Einträgen</a> für Produktübermittlungen anzeigen und bearbeiten sowie neue Store-Einträge für verschiedene Sprachen hinzufügen.     </td><td>    Kann die <a href="create-add-on-store-listings.md">Seite(n) mit Store-Einträgen</a> für Add-On-Übermittlungen anzeigen.            </td><td>    Kann die <a href="create-add-on-store-listings.md">Seite(n) mit Store-Einträgen</a> für Add-On-Übermittlungen anzeigen und bearbeiten sowie neue Store-Einträge für verschiedene Sprachen hinzufügen.                 </td></tr>
    <tr><td align="left">    <b>Store-Übermittlung</b>     </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.           </td><td>    Kann das Produkt an den Store übermitteln und Zertifizierungsberichte anzeigen. Dies gilt sowohl für neue als auch für aktualisierte Übermittlungen. </td><td>Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.     </td><td>    Kann das Add-On an den Store übermitteln und Zertifizierungsberichte anzeigen. Dies gilt sowohl für neue als auch für aktualisierte Übermittlungen.</td></tr>
    <tr><td align="left">    <b>Erstellen von neuen Übermittlungen</b>       </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.        </td><td>    Kann neue <a href="app-submissions.md">Übermittlungen</a> für das Produkt erstellen.  </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist.   </td><td>    Kann neue <a href="add-on-submissions.md">Übermittlungen</a> für das Add-On erstellen.        </td></tr>
    <tr><td align="left">    <b>Neue Add-Ons</b>    </td><td>    Es wird kein Zugriff gewährt, wenn diese Berechtigung als schreibgeschützt festgelegt ist. </td><td>    Kann neue <a href="set-your-add-on-product-id.md">Add-Ons</a> für das Produkt erstellen. </td><td>    Nicht verfügbar    </td><td>    Nicht verfügbar        </td></tr>
    <tr><td align="left">    <b>Namensreservierungen</b>   </td><td>    Kann die Seite <a href="manage-app-names.md">App-Namen verwalten</a> für das Produkt anzeigen.</td><td>    Kann die Seite <a href="manage-app-names.md">App-Namen verwalten</a> für das Produkt anzeigen und bearbeiten sowie zusätzliche Namen reservieren und reservierte Namen löschen. </td><td>   Kann reservierte Namen für das Add-On anzeigen.    </td><td>   Kann reservierte Namen für das Add-On anzeigen und bearbeiten.          </td></tr>
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
    <tr><td align="left">    <b>App-Kanäle</b>&nbsp;*</td><td>    n.a.  </td><td>    Kann Werbevideokanäle auf der Xbox-Konsole für die Anzeige über OneGuide veröffentlichen.  </td><td>  Nicht verfügbar </td><td> n.a. </td></tr>
    <tr><td align="left">    <b>Dienstkonfiguration</b>&nbsp;*    </td><td>    Kann Einstellungen für Erfolge, Multiplayer, Bestenlisten und weitere Xbox Live-Konfigurationsoptionen für das Produkt anzeigen.  </td><td>    Kann Einstellungen für Erfolge, Multiplayer, Bestenlisten und weitere Xbox Live-Konfigurationsoptionen für das Produkt anzeigen und bearbeiten.  </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar                      </td></tr>
</tbody>
</table>

\ * Mit einem Sternchen (*) gekennzeichnete Berechtigungen gewähren Zugriff auf Features, die nicht für alle Konten verfügbar sind. Wenn Ihr Konto nicht für diese Features aktiviert wurde, ist Ihre Auswahl für diese Berechtigungen nicht wirksam.  
