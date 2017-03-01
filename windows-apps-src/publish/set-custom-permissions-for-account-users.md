---
author: jnHs
Description: "Legen Sie benutzerdefinierte Berechtigungen für Kontenbenutzer fest."
title: "Festlegen benutzerdefinierter Berechtigungen für Kontenbenutzer"
ms.assetid: 99f3aa18-98b4-4919-bd7b-d78356b0bf78
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 23d8c14bfdbfc05a1397fa67cb831d38ec092233
ms.lasthandoff: 02/08/2017

---

# <a name="set-custom-permissions-for-account-users"></a>Festlegen benutzerdefinierter Berechtigungen für Kontenbenutzer

Wenn Sie Ihrem Konto Benutzer hinzufügen, können Sie diesen eine [Standardrolle](manage-account-users.md#roles-and-permissions) zuweisen oder die Berechtigungen so anpassen, dass die Benutzer über die entsprechende Zugriffsebene verfügen. Einige dieser Berechtigungen gelten für das gesamte Konto, während andere für alle Produkte erteilt oder auf bestimmte Produkte beschränkt werden können. 

Um anstelle von Standardrollen benutzerdefinierte Berechtigungen zu verwenden, klicken Sie beim Hinzufügen oder Bearbeiten des Benutzerkontos im Abschnitt **Rollen** auf **Berechtigungen anpassen**. 

> **Hinweis** Unabhängig davon, ob Sie einen Benutzer, eine Gruppe oder eine Azure AD-Anwendung hinzufügen, können die gleichen Berechtigungen übernommen werden.

Um eine Berechtigung für den Benutzer zu aktivieren, aktivieren Sie das Kontrollkästchen für die entsprechende Einstellung. 

![Anleitung für die Zugriffseinstellungen](images/permission_key.png)

- **Kein Zugriff**: Der Benutzer verfügt nicht über die angegebene Berechtigung.
- **Schreibgeschützt**: Der Benutzer kann Features im Zusammenhang mit dem angegebenen Bereich anzeigen, sie jedoch nicht ändern.
- **Lese-/Schreibzugriff**: Der Benutzer kann für den Bereich Änderungen vornehmen sowie diesen anzeigen.
- **Gemischt**: Diese Option kann nicht direkt ausgewählt werden. **Gemischt** ist jedoch verfügbar, wenn Sie für die Berechtigung eine Zugriffskombination zugelassen haben. Wenn Sie z. B. **Schreibgeschützt** bei **Preise und Verfügbarkeit** für **Alle Produkte** festlegen, anschließend jedoch **Lese-/Schreibzugriff** auf **Preise und Verfügbarkeit** für ein bestimmtes Produkt gewähren, wird für **Preise und Verfügbarkeit** unter **Alle Produkte** „Gemischt“ angezeigt. Dasselbe gilt, wenn für einige Produkte als Berechtigung **Kein Zugriff** festgelegt ist, für andere jedoch **Lese-/Schreibzugriff** und/oder **Schreibgeschützt**.

Für einige Berechtigungen (z. B. im Zusammenhang mit dem Anzeigen von Analysedaten) kann nur Lesezugriff (**Schreibgeschützt**) gewährt werden. Beachten Sie, dass in der aktuellen Implementierung bei einigen Berechtigungen keine Unterscheidung zwischen **Schreibgeschützt** und **Lese-/Schreibzugriff** besteht. Ein besseres Verständnis der jeweiligen Funktionen, die mit **Schreibgeschützt** und **Lese-/Schreibzugriff** gewährt werden, erhalten Sie anhand der Details zu den einzelnen Berechtigungen.

Die Details der einzelnen Berechtigungen werden in den folgenden Tabellen beschrieben.

## <a name="account-level-permissions"></a>Berechtigungen auf Kontoebene

Die Berechtigungen in diesem Abschnitt können nicht auf bestimmte Produkte beschränkt werden. Wird dem Benutzer Zugriff auf diese Berechtigungen gewährt, gilt dies für das gesamte Konto.

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
<tr><td align="left">    **Kontenbenutzer**                       </td><td align="left">  Kann Benutzer anzeigen, die dem Konto im Abschnitt **Benutzer verwalten** hinzugefügt wurden.          </td><td align="left">  Kann dem Konto Benutzer hinzufügen und im Abschnitt **Benutzer verwalten** Änderungen an vorhandenen Benutzern vornehmen.             </td></tr>
<tr><td align="left">    **Bericht zur Anzeigenleistung auf Kontoebene** </td><td align="left">  Kann den [Bericht zur Anzeigenleistung auf Kontoebene](advertising-performance-report.md#account-level-advertising-performance-report) anzeigen. (Kann keine Berichte zur Anzeigenleistung für einzelne Produkte anzeigen, sofern diese Berechtigung nicht separat erteilt wurde.)       </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    **Anzeigenkampagnen**                        </td><td align="left">  Kann im Konto erstellte [Anzeigenkampagnen](create-an-ad-campaign-for-your-app.md) anzeigen.      </td><td align="left">  Kann im Konto erstellte [Anzeigenkampagnen](create-an-ad-campaign-for-your-app.md) erstellen, verwalten und anzeigen.          </td></tr>
<tr><td align="left">    **Anzeigenvermittlung**                        </td><td align="left">  Kann [Anzeigenvermittlungskonfigurationen](https://msdn.microsoft.com/library/windows/apps/xaml/mt149935.aspx) für alle Produkte des Kontos anzeigen.    </td><td align="left">  Kann [Anzeigenvermittlungskonfigurationen](https://msdn.microsoft.com/library/windows/apps/xaml/mt149935.aspx) für alle Produkte des Kontos anzeigen und ändern.        </td></tr>
<tr><td align="left">    **Berichte zur Anzeigenvermittlung**                </td><td align="left">  Kann den [Bericht zur Anzeigenvermittlung](ad-mediation-report.md) für alle Produkte des Kontos anzeigen.    </td><td align="left">  Nicht verfügbar    </td></tr>
<tr><td align="left">    **Berichte zur Anzeigenleistung**              </td><td align="left">  Kann [Berichte zur Anzeigenleistung](advertising-performance-report.md) für alle Produkte des Kontos anzeigen. (Kann den [Bericht zur Anzeigenleistung](advertising-performance-report.md#account-level-advertising-performance-report) auf Kontoebene nicht anzeigen, sofern diese Berechtigung nicht separat erteilt wurde.)       </td><td align="left">  Kann [Berichte zur Anzeigenleistung](advertising-performance-report.md) für alle Produkte des Kontos anzeigen. (Kann den [Bericht zur Anzeigenleistung](advertising-performance-report.md#account-level-advertising-performance-report) auf Kontoebene nicht anzeigen, sofern diese Berechtigung nicht separat erteilt wurde.)         </td></tr>
<tr><td align="left">    **Anzeigeneinheiten**                            </td><td align="left">  Kann die für das Konto erstellten [Anzeigeneinheiten](monetize-with-ads.md) anzeigen.    </td><td align="left">  Kann [Anzeigeneinheiten](monetize-with-ads.md) für das Konto erstellen, verwalten und anzeigen.             </td></tr>
<tr><td align="left">    **Partneranzeigen**                       </td><td align="left">  Kann die Nutzung von [Partneranzeigen](about-affiliate-ads.md) für alle Produkte des Kontos anzeigen.    </td><td align="left">  Kann die Nutzung von [Partneranzeigen](about-affiliate-ads.md) für alle Produkte des Kontos verwalten und anzeigen.                </td></tr>
<tr><td align="left">    **Berichte zur Partneranzeigenleistung**      </td><td align="left">  Kann den [Bericht zur Partneranzeigenleistung](affiliates-performance-report.md) für alle Produkte des Kontos anzeigen.   </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    **Berichte „Anzeigen für die App-Installation“**             </td><td align="left">  Kann den [Bericht „Anzeigen für die App-Installation“](app-install-ads-reports.md) für alle Produkte des Kontos anzeigen.           </td><td align="left">  Nicht verfügbar   </td></tr>
<tr><td align="left">    **Community-Anzeigen**                       </td><td align="left">  Kann die Nutzung kostenloser [Community-Anzeigen](about-community-ads.md) für alle Produkte des Kontos anzeigen.          </td><td align="left">  Kann die Nutzung kostenloser [Community-Anzeigen](about-community-ads.md) für alle Produkte des Kontos erstellen, verwalten und anzeigen.               </td></tr>
<tr><td align="left">    **Kontaktinformationen**                        </td><td align="left">  Kann [Kontaktinformationen](managing-your-profile.md) im Abschnitt mit den Kontoeinstellungen anzeigen.        </td><td align="left">  Kann [Kontaktinformationen](managing-your-profile.md) im Abschnitt mit den Kontoeinstellungen anzeigen und bearbeiten.            </td></tr>
<tr><td align="left">    **COPPA-Compliance**                    </td><td align="left">  Kann für alle Produkte des Kontos die Einstellungen für die [COPPA-Compliance](monetize-with-ads.md#coppa-compliance) anzeigen (die angeben, ob sich Produkte an Kinder unter 13 Jahren richten).                                            </td><td align="left">  Kann für alle Produkte des Kontos die Einstellungen für die [COPPA-Compliance](monetize-with-ads.md#coppa-compliance) anzeigen und bearbeiten (die angeben, ob sich Produkte an Kinder unter 13 Jahren richten).         </td></tr>
<tr><td align="left">    **Kundengruppen**                     </td><td align="left">  Kann [Kundengruppen](create-customer-groups.md) (Segmente und Flight-Gruppen) im Abschnitt **Kunden** anzeigen.      </td><td align="left">  Kann [Kundengruppen](create-customer-groups.md) (Segmente und Flight-Gruppen) im Abschnitt **Kunden** erstellen, bearbeiten und anzeigen.       </td></tr>
<tr><td align="left">    **Neue Apps**                            </td><td align="left">  Kann die Seite zum Erstellen neuer Apps anzeigen, jedoch keine neuen Apps im Konto erstellen.    </td><td align="left">  Kann im Konto [neue Apps erstellen](create-your-app-by-reserving-a-name.md), indem neue App-Namen reserviert werden. Zudem können Übermittlungen erstellt und Apps an den Store übermittelt werden.     </td></tr>
<tr><td align="left">    **Neue Bündel**&nbsp;*                       </td><td align="left">  Kann die Seite zum Erstellen neuer Bündel anzeigen, jedoch keine neuen Bündel im Konto erstellen.     </td><td align="left">  Kann neue Produktbündel erstellen.          </td></tr>
<tr><td align="left">    **Partnerdienste**&nbsp;*                  </td><td align="left">  Kann Zertifikate für das Installieren in Diensten zum Abrufen von XTokens anzeigen.     </td><td align="left">  Kann Zertifikate für das Installieren in Diensten zum Abrufen von XTokens verwalten und anzeigen.       </td></tr>
<tr><td align="left">    **Auszahlungskonto**                      </td><td align="left">  Kann [Auszahlungskontodaten](setting-up-your-payout-account-and-tax-forms.md#payout-account) unter **Kontoeinstellungen** anzeigen.     </td><td align="left">  Kann [Auszahlungskontodaten](setting-up-your-payout-account-and-tax-forms.md#payout-account) unter **Kontoeinstellungen** bearbeiten und anzeigen.       </td></tr>
<tr><td align="left">    **Auszahlungsübersicht**                      </td><td align="left">  Kann die [Auszahlungsübersicht](payout-summary.md) anzeigen, um auf Auszahlungsberichtsdaten zuzugreifen und diese herunterzuladen.       </td><td align="left">  Kann die [Auszahlungsübersicht](payout-summary.md) anzeigen, um auf Auszahlungsberichtsdaten zuzugreifen und diese herunterzuladen.   </td></tr>
<tr><td align="left">    **Vertrauende Seiten**&nbsp;*                   </td><td align="left">  Kann vertrauende Seiten anzeigen, um XTokens abzurufen.    </td><td align="left">  Kann vertrauende Seiten verwalten und anzeigen, um XTokens abzurufen.     </td></tr>
<tr><td align="left">    **Sandboxes**&nbsp;*                         </td><td align="left">  Kann auf die Seite **Sandboxes** zugreifen und für das Konto die Sandboxes sowie alle gültigen Konfigurationen anzeigen. Kann nicht die Produkte und Übermittlungen für die jeweilige Sandbox anzeigen, sofern keine entsprechenden Berechtigungen auf Produktebene erteilt wurden. </td><td align="left">  Kann auf die Seite **Sandboxes** zugreifen und die Sandboxes im Konto anzeigen und verwalten, z. B. um Sandboxes zu erstellen und zu löschen oder deren Konfiguration zu verwalten. Kann nicht die Produkte und Übermittlungen für die jeweilige Sandbox anzeigen, sofern keine entsprechenden Berechtigungen auf Produktebene erteilt wurden.    </td></tr>
<tr><td align="left">    **Steuerprofil**                         </td><td align="left">  Kann [Steuerprofildaten und -formulare](setting-up-your-payout-account-and-tax-forms.md#tax-forms) in den **Kontoeinstellungen** anzeigen.     </td><td align="left">  Kann Steuerformulare ausfüllen und [Steuerprofildaten](setting-up-your-payout-account-and-tax-forms.md#tax-forms) in den **Kontoeinstellungen** aktualisieren.     </td></tr>
<tr><td align="left">    **Testkonten**&nbsp;*                     </td><td align="left">  Kann Konten zum Testen der Xbox Live-Konfiguration anzeigen.      </td><td align="left">  Kann Konten zum Testen der Xbox Live-Konfiguration erstellen, verwalten und anzeigen.      </td></tr>
<tr><td align="left">    **Xbox-Geräte**                        </td><td align="left">  Kann im Abschnitt **Kontoeinstellungen** die für das Konto aktivierten Xbox-Entwicklungskonsolen anzeigen.       </td><td align="left">  Kann die für das Konto aktivierten Xbox-Entwicklungskonsolen im Abschnitt **Kontoeinstellungen** hinzufügen, entfernen und anzeigen.     </td></tr>
    </tbody>
    </table>

\ * Mit einem Sternchen (*) gekennzeichnete Berechtigungen gewähren Zugriff auf Features, die nicht für alle Konten verfügbar sind. Wenn Ihr Konto nicht für diese Features aktiviert wurde, ist Ihre Auswahl für diese Berechtigungen nicht wirksam.   

## <a name="product-level-permissions"></a>Berechtigungen auf Produktebene

Die Berechtigungen in diesem Abschnitt können für alle Produkte im Konto erteilt werden. Zudem können sie so angepasst werden, dass sie nur für ein oder mehrere bestimmte Produkte erteilt werden. Diese Berechtigungen sind in vier Kategorien unterteilt: **Analysen**, **Monetarisierung**, **Veröffentlichung** und **Xbox Live**. Sie können die einzelnen Kategorien erweitern, um die jeweiligen Berechtigungen anzuzeigen. 

Um eine Berechtigung für alle Produkte des Kontos zu erteilen, treffen Sie in der Zeile **Alle Produkte** Ihre Auswahl für diese Berechtigung (indem Sie für das Feld **Schreibgeschützt**, **Lese-/Schreibzugriff** oder **Kein Zugriff** aktivieren). 
 
> **Tipp** Die für **Alle Produkte** getroffene Auswahl gilt für sämtliche derzeit im Konto vorhandenen Produkte sowie für alle zukünftig für das Konto erstellten Produkte.

Unterhalb der Zeile **Alle Produkte** sind die einzelnen Produkte des Kontos in jeweils eigenen Zeilen aufgeführt. Um nur für ein bestimmtes Produkt eine Berechtigung zu erteilen, treffen Sie Ihre Berechtigungsauswahl in der Zeile für das Produkt.

Jedes Add-On wird in einer separaten Zeile unterhalb des übergeordneten Produkts aufgeführt. Zudem gibt es die Zeile **Alle Add-Ons**. Die unter **Alle Add-Ons** getroffene Auswahl gilt für alle aktuellen Add-Ons des Produkts sowie für alle zukünftig für das Produkte erstellten Add-Ons.

Beachten Sie, dass einige Berechtigungen nicht für Add-Ons festgelegt werden können. Dies liegt entweder daran, dass sie nicht für Add-Ons gelten (z. B. die Berechtigung **Kundenfeedback**), oder dass die auf der Ebene des übergeordneten Produkts erteilte Berechtigung für alle Add-Ons des Produkts gilt (z. B. **Werbecodes**). Beachten Sie jedoch, dass alle für Add-Ons verfügbaren Berechtigungen separat festgelegt werden müssen. Add-Ons erben nicht die für das übergeordnete Produkt getroffene Auswahl. Wenn Sie z. B. einem Benutzer gestatten möchten, Preis- und Verfügbarkeitsoptionen für ein Add-On vorzunehmen, müssen Sie die Berechtigung **Preise und Verfügbarkeit** für das Add-On (oder für **Alle Add-Ons**) unabhängig davon aktivieren, ob Sie die Berechtigung **Preise und Verfügbarkeit** für das übergeordnete Produkt erteilt haben. 

### <a name="analytics"></a>Analysen

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der&nbsp;Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **Käufe**     </td><td>    Kann die Berichte [Käufe](acquisitions-report.md) und [Add-On-Käufe](add-on-acquisitions-report.md) für das Produkt anzeigen.        </td><td>    Nicht verfügbar    </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt umfassen Berichte zu Add-On-Käufen)        </td><td>    Nicht verfügbar                         </td></tr>
    <tr><td align="left">    **Nutzung** </td><td>    Kann den [Bericht „Nutzung“](usage-report.md) für das Produkt anzeigen.     </td><td>    Nicht verfügbar       </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    **Integrität** </td><td>    Kann den [Bericht „Integrität“](health-report.md) für das Produkt anzeigen.    </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    **Kundenfeedback**    </td><td>    Kann die Berichte [Bewertungen](ratings-report.md), [Rezensionen](reviews-report.md) und [Feedback](feedback-report.md) für das Produkt anzeigen.       </td><td>    Nicht verfügbar (Um auf Feedback oder Rezensionen reagieren zu können, muss die Berechtigung **Kunden kontaktieren** erteilt werden)   </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar         </td></tr>
    <tr><td align="left">    **Xbox-Analyse** </td><td>    Kann den Xbox-Analysebericht für das Produkt anzeigen. (Hinweis: Dieser Bericht ist noch nicht verfügbar.)    </td><td>    Nicht verfügbar   </td><td>    Nicht verfügbar       </td><td>    Nicht verfügbar          </td></tr>
    <tr><td align="left">    **Echtzeit**   </td><td>    Kann den Echtzeit-Bericht für das Produkt anzeigen.       </td><td>    Nicht verfügbar   </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar                 </td></tr>
    </tbody>
    </table>

### <a name="monetization"></a>Monetisierung

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der&nbsp;Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **Kunden kontaktieren**  </td><td>    Kann [Reaktionen auf Kundenfeedback](respond-to-customer-feedback.md) und [Antworten auf Kundenrezensionen](respond-to-customer-reviews.md) anzeigen, sofern zudem die Berechtigung **Kundenfeedback** erteilt wurde. Kann zudem für das Produkt erstellte [benutzerorientierte Benachrichtigungen](send-push-notifications-to-your-apps-customers.md) anzeigen.    </td><td>    Kann [auf Kundenfeedback reagieren](respond-to-customer-feedback.md) und [auf Kundenrezensionen antworten](respond-to-customer-reviews.md), sofern die Berechtigung **Kundenfeedback** ebenfalls erteilt wurde. Kann zudem für das Produkt [benutzerorientierte Benachrichtigungen erstellen und senden](send-push-notifications-to-your-apps-customers.md).                   </td><td>    Nicht verfügbar         </td><td>    Nicht verfügbar                          </td></tr>
    <tr><td align="left">    **Experimentation**</td><td>    Kann [Experimente (A/B-Tests)](../monetize/run-app-experiments-with-a-b-testing.md) sowie Experimentdaten für das Produkt anzeigen.   </td><td>    Kann [Experimente (A/B-Tests)](../monetize/run-app-experiments-with-a-b-testing.md) für das Produkt erstellen, verwalten und anzeigen sowie Experimentdaten anzeigen.     </td><td>    Nicht verfügbar  </td><td>    Nicht verfügbar                 </td></tr>
    <tr><td align="left">    **Werbecodes**     </td><td>    Kann Aufträge und Nutzungsdaten für [Werbecodes](generate-promotional-codes.md) für das Produkt und dessen Add-Ons anzeigen.         </td><td>    Kann Aufträge und Nutzungsdaten für [Werbecodes](generate-promotional-codes.md) für das Produkt und dessen Add-Ons anzeigen, verwalten und erstellen.          </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt gelten für alle Add-Ons)     </td><td>    Nicht verfügbar (Einstellungen für das übergeordnete Produkt gelten für alle Add-Ons)     </td></tr>
    </tbody>
    </table>

### <a name="publishing"></a>Veröffentlichung 

<table>
    <thead>
    <tr class="header">
    <th align="left">Name der&nbsp;Berechtigung</th>
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
    <th align="left">Name der&nbsp;Berechtigung</th>
    <th align="left">Schreibgeschützt</th>
    <th align="left">Lese-/Schreibzugriff</th>
    <th align="left">Schreibgeschützt&nbsp;(Add-On) </th>
    <th align="left">Lese- und Schreibzugriff&nbsp;(Add-On)</th>
    </tr>
    </thead>
    <tbody>
    <tr><td align="left">    **Xbox-Dienstkonfiguration**&nbsp;\*    </td><td>    Kann Einstellungen für Erfolge, Multiplayer, Bestenlisten und weitere Xbox Live-Konfigurationsoptionen für das Produkt anzeigen.  </td><td>    Kann Einstellungen für Erfolge, Multiplayer, Bestenlisten und weitere Xbox Live-Konfigurationsoptionen für das Produkt anzeigen und bearbeiten.  </td><td>    Nicht verfügbar     </td><td>    Nicht verfügbar                      </td></tr>
    <tr><td align="left">    **App-Kanäle**&nbsp;\*</td><td>    Nicht verfügbar  </td><td>    Kann Werbevideokanäle auf der Xbox-Konsole für die Anzeige über OneGuide veröffentlichen.  </td><td>  Nicht verfügbar </td><td> Nicht verfügbar </td></tr>
</tbody>
</table>

\ * Mit einem Sternchen (*) gekennzeichnete Berechtigungen gewähren Zugriff auf Features, die nicht für alle Konten verfügbar sind. Wenn Ihr Konto nicht für diese Features aktiviert wurde, ist Ihre Auswahl für diese Berechtigungen nicht wirksam.  

