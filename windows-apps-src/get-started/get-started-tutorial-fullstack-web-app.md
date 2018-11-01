---
author: libbymc
title: Erstellen einer Web-App mit einer einzelnen Seite mit REST API-Backend
description: Verwenden Sie beliebte Webtechnologien zum Erstellen einer gehosteten Web-App für den Microsoft Store
keywords: Gehostete Web-App, HWA, REST-API, Einzelseiten-App, SPA
ms.author: libbymc
ms.date: 05/10/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 140f28949bea6b4f67730bd7f6afaed4bcfb9935
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5872957"
---
# <a name="create-a-single-page-web-app-with-rest-api-backend"></a><span data-ttu-id="970de-104">Erstellen einer Web-App mit einer einzelnen Seite mit REST API-Backend</span><span class="sxs-lookup"><span data-stu-id="970de-104">Create a single-page web app with REST API backend</span></span>

**<span data-ttu-id="970de-105">Erstellen einer gehosteten Web-App für den Microsoft Store mit gängigen Fullstack-Webtechnologien</span><span class="sxs-lookup"><span data-stu-id="970de-105">Build a Hosted Web App for the Microsoft Store with popular fullstack web technologies</span></span>**

![Einfaches Arbeitsspeicherspiel als Einzelseiten-Web-App](images/fullstack.png)

<span data-ttu-id="970de-107">Dieses zweiteilige Lernprogramm bietet einen kurzen Überblick über die moderne Fullstack-Webentwicklung, indem Sie ein einfaches Arbeitsspeicherspiel erstellen, das sowohl im Browser als auch als eine gehostete Web-App für den Microsoft Store funktioniert.</span><span class="sxs-lookup"><span data-stu-id="970de-107">This two-part tutorial provides a quick tour of modern fullstack web development as you build a simple memory game that works both in the browser and as a Hosted Web App for the Microsoft Store.</span></span> <span data-ttu-id="970de-108">In Teil I erstellen Sie einen einfachen REST-API-Dienst für das Spiel-Back-End.</span><span class="sxs-lookup"><span data-stu-id="970de-108">In Part I you'll build a simple REST API service for the game's backend.</span></span> <span data-ttu-id="970de-109">Durch das Hosten der Spiellogik in der Cloud als ein API-Dienst wird der Spielstand beibehalten, damit Ihre Benutzer ihre Spielinstanzen auf verschiedenen Geräten weiterspielen können.</span><span class="sxs-lookup"><span data-stu-id="970de-109">By hosting the game logic in the cloud as an API service, you preserve the game state so your user can keep playing their same game instance across different devices.</span></span> <span data-ttu-id="970de-110">In Teil II werden Sie die Front-End-Benutzeroberfläche als eine Einzelseiten-Web-App mit dynamischem Layout erstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-110">In Part II you'll build the front-end UI as a single-page web app with responsive layout.</span></span>

<span data-ttu-id="970de-111">Wir werden einige der beliebtesten Webtechnologien verwenden, einschließlich des [Node.js](https://nodejs.org/en/) Runtime und [Express](http://expressjs.com/) für serverseitige Entwicklung, das [Bootstrap](http://getbootstrap.com/)-UI-Framework, das [Pug](https://www.npmjs.com/package/pug)-Vorlagenmodul und [Swagger](http://swagger.io/tools/) zum Erstellen von RESTful-APIs.</span><span class="sxs-lookup"><span data-stu-id="970de-111">We'll be using some of the most popular web technologies, including the [Node.js](https://nodejs.org/en/) runtime and [Express](http://expressjs.com/) for server-side development, the [Bootstrap](http://getbootstrap.com/) UI framework, the [Pug](https://www.npmjs.com/package/pug) template engine, and [Swagger](http://swagger.io/tools/) for building RESTful APIs.</span></span> <span data-ttu-id="970de-112">Sie werden auch Erfahrung mit dem [Azure-Portal](https://ms.portal.azure.com/) für das Cloud-Hosting sammeln, und mit dem [Visual Studio Code](https://code.visualstudio.com/)-Editor arbeiten.</span><span class="sxs-lookup"><span data-stu-id="970de-112">You'll also gain experience with the [Azure Portal](https://ms.portal.azure.com/) for cloud hosting and working with the [Visual Studio Code](https://code.visualstudio.com/) editor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="970de-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="970de-113">Prerequisites</span></span>

<span data-ttu-id="970de-114">Wenn Sie diese Ressourcen nicht bereits auf dem Computer besitzen, folgen Sie den folgenden Downloadlinks:</span><span class="sxs-lookup"><span data-stu-id="970de-114">If you don't already have these resources on your machine, follow these download links:</span></span>

 - <span data-ttu-id="970de-115">[Node.js](https://nodejs.org/en/download/) – Stellen Sie sicher, dass Sie die Option für das Hinzufügen eines Knotens zu Ihrem PATH ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="970de-115">[Node.js](https://nodejs.org/en/download/) - Be sure to select the option to add Node to your PATH.</span></span>

 - <span data-ttu-id="970de-116">[Express-Generator](http://expressjs.com/en/starter/generator.html)– nach der Installation des Knotens mit Express installieren</span><span class="sxs-lookup"><span data-stu-id="970de-116">[Express generator](http://expressjs.com/en/starter/generator.html)- After you install Node, install Express by running</span></span> `npm install express-generator -g`

 - [<span data-ttu-id="970de-117">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="970de-117">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="970de-118">Wenn Sie die endgültigen Schritte zum Hosten Ihres API-Diensts und Ihrer Arbeitsspeicherspiele-App auf Microsoft Azure abschließen möchten, müssen [Sie ein kostenloses Azure-Konto erstellen](https://azure.microsoft.com/en-us/free/), wenn Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="970de-118">If you want to complete the final steps of hosting your API service and memory game app on Microsoft Azure, you'll need to [create a free Azure account](https://azure.microsoft.com/en-us/free/) if you haven't already done so.</span></span>

<span data-ttu-id="970de-119">Wenn Sie den Azure-Teil beenden (oder verschieben) möchten, überspringen Sie einfach die endgültigen Abschnitte der Teile I und II, die das Azure-Hosten und Verpacken Ihrer App für den Microsoft Store abdecken.</span><span class="sxs-lookup"><span data-stu-id="970de-119">If you decide to bail on (or postpone) the Azure part, simply skip the final sections of parts I and II, which cover Azure hosting and packaging your app for the Microsoft Store.</span></span> <span data-ttu-id="970de-120">Der API-Dienst und Web-App, die Sie erstellen, wird weiterhin lokal (entsprechend aus `http://localhost:8000` und `http://localhost:3000`) auf Ihrem Computer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="970de-120">The API service and web app you build will still run locally (from `http://localhost:8000` and `http://localhost:3000`, respectively) on your machine.</span></span>

## <a name="part-i-build-a-rest-api-backend"></a><span data-ttu-id="970de-121">Teil I: Erstellen eines REST-API-Back-Ends</span><span class="sxs-lookup"><span data-stu-id="970de-121">Part I: Build a REST API backend</span></span>

<span data-ttu-id="970de-122">Zunächst erstellen wir eine einfache Speicherspiel-API, um unsere Arbeitsspeicherspiele-Web-App anzutreiben.</span><span class="sxs-lookup"><span data-stu-id="970de-122">We'll first build a simple memory game API to power our memory game web app.</span></span> <span data-ttu-id="970de-123">Wir verwenden [Swagger](http://swagger.io/), um unsere API zu definieren und Gerüst-Code und eine Web-Benutzeroberfläche für das manuelle Testen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="970de-123">We'll use [Swagger](http://swagger.io/) to define our API and generate scaffolding code and a web UI for manual testing.</span></span>

<span data-ttu-id="970de-124">Wenn Sie diesen Abschnittüberspringen und direkt zu [Teil II: Erstellen einer Einzelseiten-Web-Anwendung](#part-ii-build-a-single-page-web-appl) fortfahren möchten, gelangen Sie hier zum [fertigen Code für Teil I](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/backend). Folgen Sie den Anweisungen der *Infodatei*, um den Code lokal auszuführen, oder finden Sie weitere Informationen unter *5. Ihren API-Dienst in Azure hosten und CORS* aktivieren, um ihn in Azure auszuführen.</span><span class="sxs-lookup"><span data-stu-id="970de-124">If you'd like to skip this part and move straight to [Part II: Build a single-page web application](#part-ii-build-a-single-page-web-appl), here's the [finished code for Part I](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/backend). Follow the *README* instructions to get the code up and running locally, or see *5. Host your API service on Azure and enable CORS* to run it from Azure.</span></span>

### <a name="game-overview"></a><span data-ttu-id="970de-125">Spielübersicht</span><span class="sxs-lookup"><span data-stu-id="970de-125">Game overview</span></span>

<span data-ttu-id="970de-126">*Arbeitsspeicher* (auch bekannt als [*Konzentration*](https://en.wikipedia.org/wiki/Concentration_(game)) und [*Pelmanism*](https://en.wikipedia.org/wiki/Pelmanism_(system))), ist ein einfaches Spiel aus einem Kartenspiel mit Kartenpaaren.</span><span class="sxs-lookup"><span data-stu-id="970de-126">*Memory* (also known as [*Concentration*](https://en.wikipedia.org/wiki/Concentration_(game)) and [*Pelmanism*](https://en.wikipedia.org/wiki/Pelmanism_(system))), is a simple game consisting of a deck of card pairs.</span></span> <span data-ttu-id="970de-127">Die Karten werden verdeckt auf den Tisch platziert. Der Spieler prüft die Kartenwerte, zwei Karten gleichzeitig, und sucht nach Übereinstimmungen.</span><span class="sxs-lookup"><span data-stu-id="970de-127">The cards are placed face-down on the table, and the player inspects the card values, two at a time, looking for matches.</span></span> <span data-ttu-id="970de-128">Nach jeder Runde werden die Karten erneut verdeckt auf den Tisch gelegt, sofern kein übereinstimmendes Paar gefunden wurde. Wird ein Paar gefunden, werden die zwei Karten aus dem Spiel entfernt.</span><span class="sxs-lookup"><span data-stu-id="970de-128">After each turn the cards are again placed face-down, unless a matching pair is found, in which case those two cards are cleared from the game.</span></span> <span data-ttu-id="970de-129">Das Ziel des Spiels ist es, alle Kartenpaare in so wenig Runden wie möglich zu finden.</span><span class="sxs-lookup"><span data-stu-id="970de-129">The game objective is to find all card pairs in the fewest amount of turns.</span></span>

<span data-ttu-id="970de-130">Die von uns verwendete Spielstruktur ist zur Veranschaulichung sehr einfach: ein einziges Spiel mit einem Spieler.</span><span class="sxs-lookup"><span data-stu-id="970de-130">For instructional purposes, the game structure we'll use is very simple: it's single game, single player.</span></span> <span data-ttu-id="970de-131">Die Spiellogik erfolgt jedoch zur Bewahrung des Spielstands serverseitig (und nicht über den Client), sodass Sie dasselbe Spiel auf verschiedenen Geräten weiterspielen können.</span><span class="sxs-lookup"><span data-stu-id="970de-131">However, the game logic is server-side (rather than on the client) to preserve the game state, so that you could keep playing the same game across different devices.</span></span>

<span data-ttu-id="970de-132">Die Datenstruktur für ein Arbeitsspeicherspiel besteht einfach aus einem Array von JavaScript-Objekten, die jeweils eine einzelne Karte darstellen. Die Indizes im Array fungieren als Karten-IDs.</span><span class="sxs-lookup"><span data-stu-id="970de-132">The data structure for a memory game consists simply of an array of JavaScript objects, each representing a single card, with indices in the array acting as card IDs.</span></span> <span data-ttu-id="970de-133">Auf dem Server hat jedes Kartenobjekt einen Wert und ein **deaktiviert**-Kennzeichen.</span><span class="sxs-lookup"><span data-stu-id="970de-133">On the server, each card object has a value and a **cleared** flag.</span></span> <span data-ttu-id="970de-134">Ein Brett mit 2 Übereinstimmungen (4 Karten) können nach dem Zufallsprinzip generiert und wie folgt serialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="970de-134">For example, a board of 2-matches (4 cards) might be randomly generated and serialized like this.</span></span>

```json
[
    { "cleared":"false",
        "value":"0",
    },
    { "cleared":"false",
        "value":"1",
    },
    { "cleared":"false",
        "value":"1",
    },
    { "cleared":"false",
        "value":"0",
    }
]
```

<span data-ttu-id="970de-135">Wenn das Brett-Array an den Client übergeben wurde, werden die Werteschlüssel aus dem Array entfernt, um Täuschungen zu verhindern (z.B. Untersuchen des HTTP-Antworttexts mit Browser-Entwicklertools (F12)).</span><span class="sxs-lookup"><span data-stu-id="970de-135">When the board array is passed to the client, value keys are removed from the array to prevent cheating (for example, inspecting the HTTP response body by using F12 browser tools).</span></span> <span data-ttu-id="970de-136">So würde das gleiche neue Spiel für einen Client aussehen, der den **GET /game**-REST-Endpunkt aufruft:</span><span class="sxs-lookup"><span data-stu-id="970de-136">Here's how that same new game would look to a client calling the **GET /game** REST endpoint:</span></span>

```json
[{ "cleared":"false"},{ "cleared":"false"},{ "cleared":"false"},{ "cleared":"false"}]
```

<span data-ttu-id="970de-137">Apropos Endpunkte, der Arbeitsspeicherspiel-Dienst wird aus drei REST-APIs bestehen.</span><span class="sxs-lookup"><span data-stu-id="970de-137">Speaking of endpoints, the memory game service will consist of three REST APIs.</span></span>

#### <a name="post-new"></a><span data-ttu-id="970de-138">POST /new</span><span class="sxs-lookup"><span data-stu-id="970de-138">POST /new</span></span>
<span data-ttu-id="970de-139">Initialisiert eine neues Spielbrett in der angegebenen Größe (# der Übereinstimmungen).</span><span class="sxs-lookup"><span data-stu-id="970de-139">Initializes a new game board of the specified size (# of matches).</span></span>

| <span data-ttu-id="970de-140">Parameter</span><span class="sxs-lookup"><span data-stu-id="970de-140">Parameter</span></span> | <span data-ttu-id="970de-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="970de-141">Description</span></span> |
|-----------|-------------|
| <span data-ttu-id="970de-142">Int *Größe*</span><span class="sxs-lookup"><span data-stu-id="970de-142">int *size*</span></span> |<span data-ttu-id="970de-143">Die Anzahl der übereinstimmenden Paare, die in das „Spielbrett” gemischt wird.</span><span class="sxs-lookup"><span data-stu-id="970de-143">Number of matching pairs to be shuffled into the game "board".</span></span> <span data-ttu-id="970de-144">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="970de-144">Example:</span></span> `http://memorygameapisample/new?size=2`|

| <span data-ttu-id="970de-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="970de-145">Response</span></span> | <span data-ttu-id="970de-146">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="970de-146">Description</span></span> |
|----------|-------------|
| <span data-ttu-id="970de-147">200 OK</span><span class="sxs-lookup"><span data-stu-id="970de-147">200 OK</span></span> | <span data-ttu-id="970de-148">Neues Speicherspiel in der angeforderten Größe ist bereit.</span><span class="sxs-lookup"><span data-stu-id="970de-148">New memory game of requested size is ready.</span></span>|
| <span data-ttu-id="970de-149">400 BAD REQUEST</span><span class="sxs-lookup"><span data-stu-id="970de-149">400 BAD REQUEST</span></span>| <span data-ttu-id="970de-150">Angeforderte Größe befindet sich außerhalb des zulässigen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="970de-150">Requested size is outside of acceptable range.</span></span>|


#### <a name="get-game"></a><span data-ttu-id="970de-151">GET /game</span><span class="sxs-lookup"><span data-stu-id="970de-151">GET /game</span></span>
<span data-ttu-id="970de-152">Ruft den aktuellen Zustand des Arbeitsspeicherspiels ab.</span><span class="sxs-lookup"><span data-stu-id="970de-152">Retrieves the current state of the memory game board.</span></span>

*<span data-ttu-id="970de-153">Keine Parameter</span><span class="sxs-lookup"><span data-stu-id="970de-153">No parameters</span></span>*

| <span data-ttu-id="970de-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="970de-154">Response</span></span> | <span data-ttu-id="970de-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="970de-155">Description</span></span> |
|----------|-------------|
| <span data-ttu-id="970de-156">200 OK</span><span class="sxs-lookup"><span data-stu-id="970de-156">200 OK</span></span> | <span data-ttu-id="970de-157">Gibt JSON-Array mit Kartenobjekten zurück.</span><span class="sxs-lookup"><span data-stu-id="970de-157">Returns JSON array of card objects.</span></span> <span data-ttu-id="970de-158">Jede Karte hat eine **deaktiviert**-Eigenschaft, die angibt, ob die Übereinstimmung bereits gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="970de-158">Each card has a **cleared** property indicating whether its match has already been found.</span></span> <span data-ttu-id="970de-159">Übereinstimmende Karten melden auch ihren **Wert**.</span><span class="sxs-lookup"><span data-stu-id="970de-159">Matched cards also report their **value**.</span></span> <span data-ttu-id="970de-160">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="970de-160">Example:</span></span> `[{"cleared":"false"},{"cleared":"false"},{"cleared":"true","value":1},{"cleared":"true","value":1}]`|

#### <a name="put-guess"></a><span data-ttu-id="970de-161">PUT /guess</span><span class="sxs-lookup"><span data-stu-id="970de-161">PUT /guess</span></span>
<span data-ttu-id="970de-162">Gibt eine Karte an, die aufgedeckt werden soll, und prüft nach einer Übereinstimmung mit der zuvor aufgedeckten Karte.</span><span class="sxs-lookup"><span data-stu-id="970de-162">Specifies a card to reveal and checks for a match to the previously revealed card.</span></span>

| <span data-ttu-id="970de-163">Parameter</span><span class="sxs-lookup"><span data-stu-id="970de-163">Parameter</span></span> | <span data-ttu-id="970de-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="970de-164">Description</span></span> |
|-----------|-------------|
| <span data-ttu-id="970de-165">Int *Karte*</span><span class="sxs-lookup"><span data-stu-id="970de-165">int *card*</span></span> | <span data-ttu-id="970de-166">Karten-ID (Index im Array des Spielbretts) der Karte zum Aufdecken.</span><span class="sxs-lookup"><span data-stu-id="970de-166">Card ID (index in game board array) of the card to reveal.</span></span> <span data-ttu-id="970de-167">Jede abgeschlossene „Vermutung” besteht aus zwei angegebenen Karten (z.B. zwei Aufrufe für **/erraten** mit gültigen und eindeutigen *Karten*-Werten).</span><span class="sxs-lookup"><span data-stu-id="970de-167">Each complete "guess" consists of two specified cards (i.e., two calls to **/guess** with valid and unique *card* values).</span></span> <span data-ttu-id="970de-168">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="970de-168">Example:</span></span> `http://memorygameapisample/guess?card=0`|

| <span data-ttu-id="970de-169">Antwort</span><span class="sxs-lookup"><span data-stu-id="970de-169">Response</span></span> | <span data-ttu-id="970de-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="970de-170">Description</span></span> |
|----------|-------------|
| <span data-ttu-id="970de-171">200 OK</span><span class="sxs-lookup"><span data-stu-id="970de-171">200 OK</span></span> | <span data-ttu-id="970de-172">Gibt JSON mit gibt der **ID** und **Wert** der angegebenen Karte zurück.</span><span class="sxs-lookup"><span data-stu-id="970de-172">Returns JSON with the **id** and **value** of the specified card.</span></span> <span data-ttu-id="970de-173">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="970de-173">Example:</span></span> `[{"id":0,"value":1}]`|
| <span data-ttu-id="970de-174">400 BAD REQUEST</span><span class="sxs-lookup"><span data-stu-id="970de-174">400 BAD REQUEST</span></span> |  <span data-ttu-id="970de-175">Fehler bei der angegebenen Karte.</span><span class="sxs-lookup"><span data-stu-id="970de-175">Error with the specified card.</span></span> <span data-ttu-id="970de-176">Weitere Details finden Sie im HTTP-Antworttext.</span><span class="sxs-lookup"><span data-stu-id="970de-176">See HTTP response body for further details.</span></span>|

### <a name="1-spec-out-the-api-and-generate-code-stubs"></a><span data-ttu-id="970de-177">1. API-Spezifikationen und Generieren von Codestubs</span><span class="sxs-lookup"><span data-stu-id="970de-177">1. Spec out the API and generate code stubs</span></span>

<span data-ttu-id="970de-178">Wir verwenden [Swagger](http://swagger.io/), um den Entwurf unseres Speicherspiel-APIs in funktionieRendern Node.js-Server-Code umzuwandeln.</span><span class="sxs-lookup"><span data-stu-id="970de-178">We'll use [Swagger](http://swagger.io/) to transform the design of our memory game API into working Node.js server code.</span></span> <span data-ttu-id="970de-179">Hier erfahren Sie, wie Sie unsere [Speicherspiel-APIs als Swagger-Metadaten](https://github.com/Microsoft/Windows-tutorials-web/blob/master/Single-Page-App-with-REST-API/backend/api.json) definieren können.</span><span class="sxs-lookup"><span data-stu-id="970de-179">Here's how you might define our [memory game APIs as Swagger metadata](https://github.com/Microsoft/Windows-tutorials-web/blob/master/Single-Page-App-with-REST-API/backend/api.json).</span></span> <span data-ttu-id="970de-180">Wir werden dies benutzen, um Server-Code-Stubs zu generieren.</span><span class="sxs-lookup"><span data-stu-id="970de-180">We'll use this to generate server code stubs.</span></span>

1. <span data-ttu-id="970de-181">Erstellen Sie (z.B. in Ihrem lokalen *GitHub*-Verzeichnis) einen neuen Ordner, und laden die Datei [**API.json**](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/api.json?token=ACEfklXAHTeLkHYaI5plV20QCGuqC31cks5ZFhVIwA%3D%3D) herunter, die unsere Speicherspiel-API-Definitionen enthält.</span><span class="sxs-lookup"><span data-stu-id="970de-181">Create a new folder (in your local *GitHub* directory, for example), and download the [**api.json**](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/api.json?token=ACEfklXAHTeLkHYaI5plV20QCGuqC31cks5ZFhVIwA%3D%3D) file containing our memory game API definitions.</span></span> <span data-ttu-id="970de-182">Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="970de-182">Make sure your folder name doesn't contain any spaces.</span></span>

2. <span data-ttu-id="970de-183">Öffnen Sie Ihre Lieblings-Shell ([, oder verwenden Sie das integrierte Terminal von Visual Studio Code!](https://code.visualstudio.com/docs/editor/integrated-terminal)) in dem Ordner, und führen Sie folgenden Knoten-Paket-Manager-Befehl (NPM-Befehl) aus, um das [Yeoman](http://yeoman.io/)-Code-Gerüst-Tool (yo) und Swagger-Generator für die globale (**-g**) Knotenumgebung zu installieren:</span><span class="sxs-lookup"><span data-stu-id="970de-183">Open your favorite shell ([or use Visual Studio Code's integrated terminal!](https://code.visualstudio.com/docs/editor/integrated-terminal)) to that folder and run the following Node Package Manager (NPM) command to install the [Yeoman](http://yeoman.io/) (yo) code-scaffolding tool and Swagger generator for your global (**-g**) Node environment:</span></span>

    ```
    npm install -g yo
    npm install -g generator-swaggerize
    ```

3. <span data-ttu-id="970de-184">Jetzt können wir den Gerüst-Servercode mit Swagger generieren:</span><span class="sxs-lookup"><span data-stu-id="970de-184">Now we can generate the server scaffolding code by using Swagger:</span></span>

    ```
    yo swaggerize
    ```

4. <span data-ttu-id="970de-185">Der **swaggerize**-Befehl wird Sie einige Fragen stellen.</span><span class="sxs-lookup"><span data-stu-id="970de-185">The **swaggerize** command will ask you several questions.</span></span>
    - <span data-ttu-id="970de-186">Pfad (oder URL) zum Swagger-Dokument: **API.json**</span><span class="sxs-lookup"><span data-stu-id="970de-186">Path (or URL) to swagger document: **api.json**</span></span>
    - <span data-ttu-id="970de-187">Framework: **express**</span><span class="sxs-lookup"><span data-stu-id="970de-187">Framework: **express**</span></span>
    - <span data-ttu-id="970de-188">Wie möchten Sie dieses Projekt (YourFolderNameHere) nennen: **[EINGABETASTE]**</span><span class="sxs-lookup"><span data-stu-id="970de-188">What would you like to call this project (YourFolderNameHere): **[enter]**</span></span>

    <span data-ttu-id="970de-189">Beantworten Sie alles andere, wie Sie möchten; die Informationen sind hauptsächlich zum Angeben Ihrer Kontaktinformationen in der *package.json*-Datei, damit Sie Ihren Code als NPM-Paket verteilen können.</span><span class="sxs-lookup"><span data-stu-id="970de-189">Answer everything else as you like; the information is mostly to supply the *package.json* file with your contact info so you can distribute your code as an NPM package.</span></span>

5. <span data-ttu-id="970de-190">Zum Schluss installieren Sie alle Abhängigkeiten (gemäß der Liste in *package.json*) für Ihr neues Projekt und [Swagger UI](http://swagger.io/swagger-ui/)-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="970de-190">Finally, install all the dependencies (listed in *package.json*) for your new project and [Swagger UI](http://swagger.io/swagger-ui/) support.</span></span>

    ```
    npm install
    npm install swaggerize-ui
    ```

    <span data-ttu-id="970de-191">Starten Sie nun den VS-Code und **Datei** > **Ordner öffnen...**, und wechseln Sie zum Verzeichnis MemoryGameAPI.</span><span class="sxs-lookup"><span data-stu-id="970de-191">Now start VS Code and **File** > **Open Folder...**, and move to the MemoryGameAPI directory.</span></span> <span data-ttu-id="970de-192">Dies ist der Node.js-API-Server, den Sie gerade erstellt haben!</span><span class="sxs-lookup"><span data-stu-id="970de-192">This is the Node.js API server you just created!</span></span> <span data-ttu-id="970de-193">Er verwendet das beliebte [ExpressJS](http://expressjs.com/en/4x/api.html)-Web-Anwendungsframework zum Strukturieren und Ausführung Ihres Projekts.</span><span class="sxs-lookup"><span data-stu-id="970de-193">It uses the popular [ExpressJS](http://expressjs.com/en/4x/api.html) web application framework to structure and run your project.</span></span>

### <a name="2-customize-the-server-code-and-setup-debugging"></a><span data-ttu-id="970de-194">2. Servercode und Setup-Debugging anpassen</span><span class="sxs-lookup"><span data-stu-id="970de-194">2. Customize the server code and setup debugging</span></span>

<span data-ttu-id="970de-195">Die *Server.js*-Datei in Ihrem Projektstammverzeichnis fungiert als die „Hauptfunktion” des Servers.</span><span class="sxs-lookup"><span data-stu-id="970de-195">The *server.js* file in your project root acts as the "main" function of your server.</span></span> <span data-ttu-id="970de-196">Öffnen Sie sie im VS-Code, und fügen Sie Folgendes ein.</span><span class="sxs-lookup"><span data-stu-id="970de-196">Open it in VS Code and copy the following into it.</span></span> <span data-ttu-id="970de-197">Die vom generierten Code geänderten Zeilen sind mit weiteren Erläuterung versehen.</span><span class="sxs-lookup"><span data-stu-id="970de-197">The lines modified from the generated code are commented with further explanation.</span></span>

```javascript
'use strict';

var port = process.env.PORT || 8000; // Better flexibility than hardcoding the port

var Http = require('http');
var Express = require('express');
var BodyParser = require('body-parser');
var Swaggerize = require('swaggerize-express');
var SwaggerUi = require('swaggerize-ui'); // Provides UI for testing our API
var Path = require('path');

var App = Express();
var Server = Http.createServer(App);

App.use(function(req, res, next) {  // Enable cross origin resource sharing (for app frontend)
    res.header('Access-Control-Allow-Origin', '*');
    res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,OPTIONS');
    res.header('Access-Control-Allow-Headers', 'Content-Type, Authorization, Content-Length, X-Requested-With');

    // Prevents CORS preflight request (for PUT game_guess) from redirecting
    if ('OPTIONS' == req.method) {
      res.send(200);
    }
    else {
      next(); // Passes control to next (Swagger) handler
    }
});

App.use(BodyParser.json());
App.use(BodyParser.urlencoded({
    extended: true
}));

App.use(Swaggerize({
    api: Path.resolve('./config/swagger.json'),
    handlers: Path.resolve('./handlers'),
    docspath: '/swagger'   //  Hooks up the testing UI
}));

App.use('/', SwaggerUi({    // Serves the testing UI from our base URL
  docs: '/swagger'          //
}));

Server.listen(port, function () {  // Starts server with our modfied port settings
 });
```

<span data-ttu-id="970de-198">Damit ist es Zeit, den Server auszuführen!</span><span class="sxs-lookup"><span data-stu-id="970de-198">With that, it's time to run your server!</span></span> <span data-ttu-id="970de-199">Richten wir nun Visual Studio Code für das Debuggen von Knoten ein.</span><span class="sxs-lookup"><span data-stu-id="970de-199">Let's set up Visual Studio Code for Node debugging while we're at it.</span></span> <span data-ttu-id="970de-200">Wählen Sie auf dem **Debug** das Steuersymbol (STRG + UMSCHALT+D) und dann das Zahnradsymbol (Open launch.json) und ändern Sie „Konfigurationen” auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="970de-200">Select on the **Debug** panel icon (Ctrl+Shift+D) and then the gear icon (Open launch.json), and modify "configurations" to this:</span></span>

```json
"configurations": [
    {
        "type": "node",
        "request": "launch",
        "name": "Launch Program",
        "program": "${workspaceRoot}/server.js"
    }
]
```

<span data-ttu-id="970de-201">Drücken Sie nun F5, und öffnen Sie Ihren Browser zu [http://localhost:8000](http://localhost:8000).</span><span class="sxs-lookup"><span data-stu-id="970de-201">Now press F5 and open your browser to [http://localhost:8000](http://localhost:8000).</span></span> <span data-ttu-id="970de-202">Die Seite sollte zur Swagger-Benutzeroberfläche unserer Speicherspiel-API geöffnet werden, und von dort aus können Sie die Details und die Eingabefelder für die einzelnen Methoden erweitern.</span><span class="sxs-lookup"><span data-stu-id="970de-202">The page should open to the Swagger UI for our memory game API, and from there you can expand the details and input fields for each of the methods.</span></span> <span data-ttu-id="970de-203">Sie können sogar versuchen, die APIs aufzurufen. Deren Antworten werden jedoch nur Pseudo-Daten enthalten (bereitgestellt durch das [Swagmock](https://www.npmjs.com/package/swagmock)-Modul).</span><span class="sxs-lookup"><span data-stu-id="970de-203">You can even try calling the APIs, although their responses will contain only mocked-up data (provided by the [Swagmock](https://www.npmjs.com/package/swagmock) module).</span></span> <span data-ttu-id="970de-204">Es ist Zeit, unsere Spiellogik hinzuzufügen, um diese APIs real zu machen.</span><span class="sxs-lookup"><span data-stu-id="970de-204">It's time to add our game logic to make these APIs real.</span></span>

### <a name="3-set-up-your-route-handlers"></a><span data-ttu-id="970de-205">3. Richten Sie Ihre Routen-Handler ein.</span><span class="sxs-lookup"><span data-stu-id="970de-205">3. Set up your route handlers</span></span>

<span data-ttu-id="970de-206">Die Swagger-Datei (config\swagger.json) weist unseren Server an, wie verschiedene HTTP-Clientanforderungen durch die Zuordnung der einzelnen von ihm festgelegten URL-Pfade zu einer Handler-Datei (in \handlers) behandelt werden, und jede für den Pfad definierte Methode (z.B. **abrufen**, **POST**) zu einer `operationId` (Funktion) in der Handler-Datei.</span><span class="sxs-lookup"><span data-stu-id="970de-206">The Swagger file (config\swagger.json) instructs our server how to handle various client HTTP requests by mapping each URL path it defines to a handler file (in \handlers), and each method defined for that path (e.g., **GET**, **POST**) to an `operationId` (function) within that handler file.</span></span>

<span data-ttu-id="970de-207">In dieser Ebene unsere Programms werden wir Eingabeüberprüfungen hinzufügen, bevor wir die verschiedenen Clientanforderungen an unser Datenmodell übergeben.</span><span class="sxs-lookup"><span data-stu-id="970de-207">In this layer of our program we'll add some input checking before passing the various client requests to our data model.</span></span> <span data-ttu-id="970de-208">Herunterladen (oder kopieren und einfügen):</span><span class="sxs-lookup"><span data-stu-id="970de-208">Download (or copy and paste):</span></span>

 - <span data-ttu-id="970de-209">Dieser [game.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/handlers/game.js?token=ACEfkvhw6BUnkeSsZgnzVe086T5WLwjfks5ZFhW5wA%3D%3D)-Code für Ihre **handlers\game.js**-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-209">This [game.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/handlers/game.js?token=ACEfkvhw6BUnkeSsZgnzVe086T5WLwjfks5ZFhW5wA%3D%3D) code to your **handlers\game.js** file</span></span>
 - <span data-ttu-id="970de-210">Dieser [guess.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/handlers/guess.js?token=ACEfkswel02rHVr0e61bVsNdpv_i1Rtuks5ZFhXPwA%3D%3D)-Code für Ihre **handlers\guess.js**-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-210">This [guess.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/handlers/guess.js?token=ACEfkswel02rHVr0e61bVsNdpv_i1Rtuks5ZFhXPwA%3D%3D) code to your **handlers\guess.js** file</span></span>
 - <span data-ttu-id="970de-211">Dieser [new.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/handlers/new.js?token=ACEfkgk2QXJeRc0aaLzY5ulFsAR4Juidks5ZFhXawA%3D%3D)-Code für Ihre **handlers\new.js**-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-211">This [new.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/handlers/new.js?token=ACEfkgk2QXJeRc0aaLzY5ulFsAR4Juidks5ZFhXawA%3D%3D) code to your **handlers\new.js** file</span></span>

 <span data-ttu-id="970de-212">Sie können die Kommentare in diesen Dateien für weitere Details zu den Änderungen überfliegen, aber im Wesentlichen prüfen sie nach grundlegenden Eingabefehlern (z.B. der Client fordert ein neues Spiel mit weniger als eine Übereinstimmung an) und senden bei Bedarf aussagekräftige Fehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="970de-212">You can skim the comments in those files for more details about the changes, but in essence they check for basic input errors (for example, the client requests a new game with less than one match) and send descriptive error messages as needed.</span></span> <span data-ttu-id="970de-213">Die Handler leiten außerdem gültige Clientanforderungen an die entsprechenden Datendateien (in \data) zur weiteren Verarbeitung weiter.</span><span class="sxs-lookup"><span data-stu-id="970de-213">The handlers also route valid client requests through to their corresponding data files (in \data) for further processing.</span></span> <span data-ttu-id="970de-214">Lassen Sie uns nun mit diesen Dateien weiterarbeiten.</span><span class="sxs-lookup"><span data-stu-id="970de-214">Let's work on those next.</span></span>

### <a name="4-set-up-your-data-model"></a><span data-ttu-id="970de-215">4. Richten Sie Ihr Datenmodell ein</span><span class="sxs-lookup"><span data-stu-id="970de-215">4. Set up your data model</span></span>

<span data-ttu-id="970de-216">Es ist Zeit, den Platzhalter für den imitieRendern Dienst mit einem echten Datenmodell für unser Speicherspielbrett auszutauschen.</span><span class="sxs-lookup"><span data-stu-id="970de-216">It's time to swap out the placeholder data-mocking service with a real data model of our memory game board.</span></span>

<span data-ttu-id="970de-217">Diese Ebene unseres Programms stellt die Speicherkarten selbst dar und bietet den Großteil der Spiellogik, einschließlich das Mischen des Kartenstapel für ein neues Spiel, Erkennen von übereinstimmenden Paaren und das Verwalten des Spielzustands.</span><span class="sxs-lookup"><span data-stu-id="970de-217">This layer of our program represents the memory cards themselves and provides the bulk of the game logic, including "shuffling" the deck for a new game, identifying pairs of matched cards, and keeping track of game state.</span></span> <span data-ttu-id="970de-218">Kopieren und Einfügen:</span><span class="sxs-lookup"><span data-stu-id="970de-218">Copy and paste:</span></span>

 - <span data-ttu-id="970de-219">Dieser [game.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/data/game.js?token=ACEfksAceJNQmhF82aHjQTx78jILYKfCks5ZFhX4wA%3D%3D)-Code für Ihre **data\game.js**-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-219">This [game.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/data/game.js?token=ACEfksAceJNQmhF82aHjQTx78jILYKfCks5ZFhX4wA%3D%3D) code to your **data\game.js** file</span></span>
 - <span data-ttu-id="970de-220">Dieser [guess.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/data/guess.js?token=ACEfkvY69Zr1AZQ4iXgfCgDxeinT21bBks5ZFhYBwA%3D%3D)-Code für Ihre **data\guess.js**-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-220">This [guess.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/data/guess.js?token=ACEfkvY69Zr1AZQ4iXgfCgDxeinT21bBks5ZFhYBwA%3D%3D) code to your **data\guess.js** file</span></span>
 - <span data-ttu-id="970de-221">Dieser [new.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/data/new.js?token=ACEfkiqeDN0HjZ4-gIKRh3wfVZPSlEmgks5ZFhYPwA%3D%3D)-Code für Ihre **data\new.js**-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-221">This [new.js](https://raw.githubusercontent.com/Microsoft/Windows-tutorials-web/master/Single-Page-App-with-REST-API/backend/data/new.js?token=ACEfkiqeDN0HjZ4-gIKRh3wfVZPSlEmgks5ZFhYPwA%3D%3D) code to your **data\new.js** file</span></span>

<span data-ttu-id="970de-222">Der Einfachheit halber speichern wir unser Spielbrett in einer globalen Variable (`global.board`) auf dem Serverknoten.</span><span class="sxs-lookup"><span data-stu-id="970de-222">For simplicity, we're storing our game board in a global variable (`global.board`) on our Node server.</span></span> <span data-ttu-id="970de-223">Aber realistisch gesehen würden Sie Cloud-Speicher (z.B. Google [Cloud-Datenspeicher](https://cloud.google.com/datastore/) oder Azure [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/)) verwenden, um die Funktion in eine geeignete Speicherspiel-API-Dienst zu verwandeln, der gleichzeitig mehrere Spiele und Spieler unterstützt.</span><span class="sxs-lookup"><span data-stu-id="970de-223">But realistically you'd use cloud storage (like Google [Cloud Datastore](https://cloud.google.com/datastore/) or Azure [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/)) to make this into a viable memory-game API service that concurrently supports multiple games and players.</span></span>

<span data-ttu-id="970de-224">Stellen Sie sicher, dass Sie alle Änderungen in VS-Code gespeichert haben. Führen Sie den Server erneut aus (F5 in VS-Code oder `npm start` von Shell, und navigieren Sie dann zu [http://localhost:8000](http://localhost:8000)), um die Spiele-APIs zu testen.</span><span class="sxs-lookup"><span data-stu-id="970de-224">Make sure you've saved all the changes in VS Code, fire up your server again (F5 in VS Code or `npm start` from shell, and then browse to [http://localhost:8000](http://localhost:8000)) to test out the game API.</span></span>

<span data-ttu-id="970de-225">Jedes Mal beim Drücken der **Probieren Sie es aus!**</span><span class="sxs-lookup"><span data-stu-id="970de-225">Each time you press the **Try it out!**</span></span> <span data-ttu-id="970de-226">Schaltfläche auf einem der **/Spiele**-, **/erraten**-, oder **/ neue** Vorgänge, überprüfen Sie den resultieRendern **Antworttext** und **Antwortcode** unten, um sicherzustellen, dass alles wie erwartet funktioniert.</span><span class="sxs-lookup"><span data-stu-id="970de-226">button on one of the **/game**, **/guess**, or **/new** operations, check the resulting **Response Body** and **Response Code** below to verify that everything's working as expected.</span></span>

<span data-ttu-id="970de-227">Versuchen Sie:</span><span class="sxs-lookup"><span data-stu-id="970de-227">Try:</span></span> 

1. <span data-ttu-id="970de-228">Ein neues `size=2` Spiel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-228">Creating a new `size=2` game.</span></span>

    ![Ein neues Speicherspiel von der Swagger-Benutzeroberfläche zu starten.](images/swagger_new.png)

2. <span data-ttu-id="970de-230">Ein paar Werte zu erraten.</span><span class="sxs-lookup"><span data-stu-id="970de-230">Guessing a couple of values.</span></span>

    ![Eine Karte auf der Swagger-Benutzeroberfläche zu erraten.](images/swagger_guess.png)

3. <span data-ttu-id="970de-232">Das Spielbrett während des Spiels zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="970de-232">Checking the game board as the game progresses.</span></span>

    ![Aus der Swagger-Benutzeroberfläche den Spielzustand zu überprüfen.](images/swagger_game.png)

<span data-ttu-id="970de-234">Wenn alles gut aussieht, kann Ihr API-Dienst auf Azure gehostet werden!</span><span class="sxs-lookup"><span data-stu-id="970de-234">If everything looks good, your API service is ready to host on Azure!</span></span> <span data-ttu-id="970de-235">Wenn Probleme auftreten, versuchen Sie, mit den folgenden Zeilen in \data\game.js zu kommentieren.</span><span class="sxs-lookup"><span data-stu-id="970de-235">If you're running into problems, try commenting out the following lines in \data\game.js.</span></span>

```javascript
for (var i=0; i < board.length; i++){
    var card = {};
    card.cleared = board[i].cleared;

    // Only reveal cleared card values
    //if ("true" == card.cleared) {        // To debug the board, comment out this line
        card.value = board[i].value;
    //}                                    // And this line
    currentBoardState.push(card);
}
```

<span data-ttu-id="970de-236">Mit dieser Änderung wird die **GET /game**-Methode alle Kartenwerte (einschließlich diejenigen, die noch nicht gelöscht wurden) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="970de-236">With this change, the **GET /game** method will return all the card values (including the ones that haven't been cleared).</span></span> <span data-ttu-id="970de-237">Hierbei handelt es sich um einen hilfreichen Debug-Hack, den Sie beim Erstellen des Front-Ends Ihres Spiels aufbewahren können.</span><span class="sxs-lookup"><span data-stu-id="970de-237">This is a useful debug hack to keep in place as you build the front-end for the memory game.</span></span>

### <a name="5-optional-host-your-api-service-on-azure-and-enable-cors"></a><span data-ttu-id="970de-238">5. (Optional) Hosten Sie Ihren API-Dienst in Azure und aktivieren Sie CORS</span><span class="sxs-lookup"><span data-stu-id="970de-238">5. (Optional) Host your API service on Azure and enable CORS</span></span>

<span data-ttu-id="970de-239">Mit der Azure-Dokumentation begleitet Sie beim:</span><span class="sxs-lookup"><span data-stu-id="970de-239">The Azure docs will walk you through:</span></span>

 - [<span data-ttu-id="970de-240">Registrieren einer neuen *API-App* mit Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="970de-240">Registering a new *API App* with Azure Portal</span></span>](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-rest-api#createapiapp)
 - <span data-ttu-id="970de-241">[Einrichten von Git-Bereitstellung für Ihre API-App](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-rest-api#deploy-the-api-with-git), und</span><span class="sxs-lookup"><span data-stu-id="970de-241">[Setting up Git deployment for your API app](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-rest-api#deploy-the-api-with-git), and</span></span>
 - [<span data-ttu-id="970de-242">Bereitstellen von API-App-Code in Azure</span><span class="sxs-lookup"><span data-stu-id="970de-242">Deploying your API app code to Azure</span></span>](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-rest-api#deploy-the-api-with-git)

<span data-ttu-id="970de-243">Versuchen Sie bei der Registrierung Ihrer App Ihren *App-Namen* zu differenzieren (zum Vermeiden von Überschneidungen mit anderen, die Varianten unter *http://memorygameapi.azurewebsites.net* URL anfordern).</span><span class="sxs-lookup"><span data-stu-id="970de-243">When registering your app, try to differentiate your *App name* (to avoid naming collisions with others requesting variations on the *http://memorygameapi.azurewebsites.net* URL).</span></span>

<span data-ttu-id="970de-244">Wenn sie es bis hier hin geschafft haben und Azure jetzt die Swagger-Benutzeroberfläche anzeigt, gibt nur noch einen letzten Schrittfür das Arbeitsspeicherspiel-Back-End.</span><span class="sxs-lookup"><span data-stu-id="970de-244">If you've made it this far and Azure is now serving up your swagger UI, there's just one final step to the memory game backend.</span></span> <span data-ttu-id="970de-245">Von [Azure-Portal](https://portal.azure.com), wählen Sie den neu erstellten *App-Dienst* und dann wählen oder suchen Sie nach der **CORS**-Option (Cross-Origin Resource Sharing).</span><span class="sxs-lookup"><span data-stu-id="970de-245">From [Azure Portal](https://portal.azure.com), select your newly created *App Service* and then select or search for the **CORS** (Cross-Origin Resource Sharing) option.</span></span> <span data-ttu-id="970de-246">Fügen Sie unter **Zulässige Ursprünge** ein Sternchen (`*`) hinzu und klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="970de-246">Under **Allowed Origins**, add an asterisk (`*`) and click **Save**.</span></span> <span data-ttu-id="970de-247">Auf diese Weise können Sie ursprungsübergreifende Aufrufe Ihrer API-Dienste aus dem Arbeitsspeicherspiel-Front-End während der Entwicklung auf dem lokalen Computer durchführen.</span><span class="sxs-lookup"><span data-stu-id="970de-247">This lets you make cross-origin calls to your API service from your memory-game front-end as you develop it on your local machine.</span></span> <span data-ttu-id="970de-248">Nach dem Abschließen des Speicherspiel-Front-Ends und das Bereitstellen auf Azure können Sie diesen Eintrag mit der bestimmten URL Ihrer Web-App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="970de-248">Once you finalize the memory-game front-end and deploy that to Azure, you can replace this entry with the specific URL of your web app.</span></span>

### <a name="going-further"></a><span data-ttu-id="970de-249">Vertiefung</span><span class="sxs-lookup"><span data-stu-id="970de-249">Going further</span></span>

<span data-ttu-id="970de-250">Um die Speicherspiel-API als einen geeigneten Back-End-Dienst für eine Produktions-App bereitzustellen, sollten Sie den Code zur Unterstützung von mehreren Spielern und Spiele erweitern.</span><span class="sxs-lookup"><span data-stu-id="970de-250">To make the memory game API a viable back-end service for a production app, you'll want to extend the code to support multiple players and games.</span></span> <span data-ttu-id="970de-251">Dazu müssen Sie wahrscheinlich die [Authentifizierung](http://swagger.io/docs/specification/authentication/) (für die Verwaltung von Spieleridentitäten), eine [NoSQL-Datenbank](https://docs.microsoft.com/en-us/azure/documentdb/) (für die Verfolgung von Spielen und Spieler), und einige grundlegenden [Unittest](https://apigee.com/about/blog/developer/swagger-test-templates-test-your-apis) für Ihre API gruppieren.</span><span class="sxs-lookup"><span data-stu-id="970de-251">For that you'll probably need to plumb in [authentication](http://swagger.io/docs/specification/authentication/) (for managing player identities), a [NoSQL database](https://docs.microsoft.com/en-us/azure/documentdb/) (for tracking games and players), and some basic [unit testing](https://apigee.com/about/blog/developer/swagger-test-templates-test-your-apis) for your API.</span></span>

<span data-ttu-id="970de-252">Hier sind einige nützliche Ressourcen für die weiterfühRendern Schritte:</span><span class="sxs-lookup"><span data-stu-id="970de-252">Here are some useful resources for going further:</span></span>

 - [<span data-ttu-id="970de-253">Erweitertes Node.js-Debugging mit Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="970de-253">Advanced Node.js debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

 - [<span data-ttu-id="970de-254">Azure Web + Mobile Dokumente</span><span class="sxs-lookup"><span data-stu-id="970de-254">Azure Web + Mobile docs</span></span>](https://docs.microsoft.com/en-us/azure/#pivot=services&panel=web)

 - [<span data-ttu-id="970de-255">Azure DocumentDB-Dokumente</span><span class="sxs-lookup"><span data-stu-id="970de-255">Azure DocumentDB docs</span></span>](https://docs.microsoft.com/en-us/azure/documentdb/index)

## <a name="part-ii-build-a-single-page-web-application"></a><span data-ttu-id="970de-256">Teil II: Erstellen einer Einzelseiten-Web-Anwendungs</span><span class="sxs-lookup"><span data-stu-id="970de-256">Part II: Build a single-page web application</span></span>

<span data-ttu-id="970de-257">Nun, da Sie mit dem Erstellen (oder [Herunterladen](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/backend)) des [REST-API-Back-Ends](#part-i-build-a-rest-api-backend) aus Teil I fertig sind, sind Sie bereit, um das Einzelseiten-Speicherspiel-Front-End mit [Knoten](https://nodejs.org/en/), [Express](http://expressjs.com/), und [Bootstrap](http://getbootstrap.com/) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-257">Now that you've built (or [downloaded](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/backend)) the [REST API backend](#part-i-build-a-rest-api-backend) from Part I,  you're ready to create the single-page memory game front-end with [Node](https://nodejs.org/en/), [Express](http://expressjs.com/), and [Bootstrap](http://getbootstrap.com/).</span></span>

<span data-ttu-id="970de-258">Teil II dieses Lernprogramms wird Ihnen folgende Kenntnisse übermitteln:</span><span class="sxs-lookup"><span data-stu-id="970de-258">Part II of this tutorial will give you experience with:</span></span> 

* <span data-ttu-id="970de-259">[Node.js](https://nodejs.org/en/): Für das Erstellen des Servers, der Ihr Spiel hostet</span><span class="sxs-lookup"><span data-stu-id="970de-259">[Node.js](https://nodejs.org/en/): to create the server hosting your game</span></span>
* <span data-ttu-id="970de-260">[jQuery](http://jquery.com/): eine JavaScript-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="970de-260">[jQuery](http://jquery.com/): a JavaScript library</span></span>
* <span data-ttu-id="970de-261">[Express](http://expressjs.com/): für das Web-Anwendungsframework</span><span class="sxs-lookup"><span data-stu-id="970de-261">[Express](http://expressjs.com/): for the web application framework</span></span>
* <span data-ttu-id="970de-262">[Pug](https://pugjs.org/): (ehemals Jade) für das Vorlagenmodul</span><span class="sxs-lookup"><span data-stu-id="970de-262">[Pug](https://pugjs.org/): (formerly Jade) for the templating engine</span></span>
* <span data-ttu-id="970de-263">[Bootstrap](http://getbootstrap.com/): für das dynamische Layout</span><span class="sxs-lookup"><span data-stu-id="970de-263">[Bootstrap](http://getbootstrap.com/): for the responsive layout</span></span>
* <span data-ttu-id="970de-264">[Visual Studio Code](https://code.visualstudio.com/): Für das Schreiben von Code, Anzeigen des Markdowns und das Debugging</span><span class="sxs-lookup"><span data-stu-id="970de-264">[Visual Studio Code](https://code.visualstudio.com/): for code authoring, markdown viewing, and debugging</span></span>

### <a name="1-create-a-nodejs-application-by-using-express"></a><span data-ttu-id="970de-265">1. Erstellen Sie eine Node.js-Anwendung mit Express</span><span class="sxs-lookup"><span data-stu-id="970de-265">1. Create a Node.js application by using Express</span></span>

<span data-ttu-id="970de-266">Beginnen wir mit der Erstellung des Node.js-Projekts mithilfe von Express.</span><span class="sxs-lookup"><span data-stu-id="970de-266">Let's start by creating the Node.js project using Express.</span></span>

1. <span data-ttu-id="970de-267">Öffnen Sie ein Eingabeaufforderungsfenster und navigieren Sie zu dem Verzeichnis, in dem Sie Ihr Spiel speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="970de-267">Open a command prompt and navigate to the directory where you want to store your game.</span></span> 
2. <span data-ttu-id="970de-268">Verwenden Sie den Express-Generator Zum Erstellen einer neuen Anwendung namens *Speicher* mithilfe des Vorlagenmoduls *Pug*.</span><span class="sxs-lookup"><span data-stu-id="970de-268">Use the Express generator to create a new application called *memory* using the templating engine, *Pug*.</span></span>

    ```
    express --view=pug memory
    ```

3. <span data-ttu-id="970de-269">Installieren Sie im Arbeitsspeicherverzeichnis die in der Datei package.json aufgeführten Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="970de-269">In the memory directory, install the dependencies listed in the package.json file.</span></span> <span data-ttu-id="970de-270">Die package.json-Datei wird im Stamm des Projekts erstellt.</span><span class="sxs-lookup"><span data-stu-id="970de-270">The package.json file is created in the root of your project.</span></span> <span data-ttu-id="970de-271">Diese Datei enthält die Module, die für Ihre Node.js-App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="970de-271">This file contains the modules that are required for your Node.js app.</span></span>  

    ```
    cd memory
    npm install
    ```

    <span data-ttu-id="970de-272">Nach dem Ausführen dieses Befehls sollte Ihnen ein Ordner namens Node_modules angezeigt werden, der alle für diese App benötigten Module enthält.</span><span class="sxs-lookup"><span data-stu-id="970de-272">After running this command, you should see a folder called node_modules that contains all of the modules needed for this app.</span></span> 

4. <span data-ttu-id="970de-273">Führen Sie nun Ihre Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="970de-273">Now, run your application.</span></span>

    ```
    npm start
    ```

5. <span data-ttu-id="970de-274">Zeigen Sie Ihre Anwendung an, indem Sie zu [http://localhost:3000/](http://localhost:3000/) wechseln.</span><span class="sxs-lookup"><span data-stu-id="970de-274">View your application by going to [http://localhost:3000/](http://localhost:3000/).</span></span>

    ![Screenshot von http://localhost:3000/-Ansichten](./images/express.png)

6. <span data-ttu-id="970de-276">Ändern Sie den Standardtitel Ihrer Web-App durch Ändern von Index.js im Verzeichnis Memory\routes.</span><span class="sxs-lookup"><span data-stu-id="970de-276">Change the default title of your web app by editing index.js in the memory\routes directory.</span></span> <span data-ttu-id="970de-277">Ändern Sie `Express` in der unten stehenden Zeile zu `Memory Game` (oder einen anderen Titel Ihrer Wahl).</span><span class="sxs-lookup"><span data-stu-id="970de-277">Change `Express` in the line below to `Memory Game` (or another title of your choosing).</span></span>

    ``` javascript
    res.render('index', { title: 'Express' });
    ```

7. <span data-ttu-id="970de-278">Beenden Sie Ihre App zum Aktualisieren der App und zum Anzeigen Ihres neues Titels durch Drücken von **STRG+C**, **Y** in der Befehlszeile, und starten Sie sie mit `npm start` neu.</span><span class="sxs-lookup"><span data-stu-id="970de-278">To refresh the app to see your new title, stop your app by pressing **Crtl + C**, **Y** in the command prompt, and then restart it with `npm start`.</span></span>

### <a name="2-add-client-side-game-logic-code"></a><span data-ttu-id="970de-279">2. Fügen Sie die clientseitigen Spiellogik-Code hinzu</span><span class="sxs-lookup"><span data-stu-id="970de-279">2. Add client-side game logic code</span></span>
<span data-ttu-id="970de-280">Sie finden die Dateien, die Sie für diese Hälfte des Lernprogramms benötigen, im [Start](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/frontend/Start)-Ordner.</span><span class="sxs-lookup"><span data-stu-id="970de-280">You can find the files you need for this half of the tutorial in the [Start](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/frontend/Start) folder.</span></span> <span data-ttu-id="970de-281">Wenn Sie sich verirren, steht der fertige Code im [endgültigen](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/frontend/Final) Ordner zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="970de-281">If you get lost, the finished code is available in the [Final](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/frontend/Final) folder.</span></span> 

1. <span data-ttu-id="970de-282">Kopieren Sie die Datei scripts.js in den [Start](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/frontend/Start)-Ordner und fügen Sie ihn in memory\public\javascripts ein.</span><span class="sxs-lookup"><span data-stu-id="970de-282">Copy the scripts.js file inside of the [Start](https://github.com/Microsoft/Windows-tutorials-web/tree/master/Single-Page-App-with-REST-API/frontend/Start) folder and paste it in memory\public\javascripts.</span></span> <span data-ttu-id="970de-283">Diese Datei enthält die gesamte Spiellogik, die zum Ausführen des Spiels erforderlich ist, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="970de-283">This file contains all the game logic needed to run the game, including:</span></span>

    * <span data-ttu-id="970de-284">Erstellen/Starten eines neuen Spiels.</span><span class="sxs-lookup"><span data-stu-id="970de-284">Creating/starting a new game.</span></span>
    * <span data-ttu-id="970de-285">Wiederherstellen eines Spiels, das auf dem Server gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="970de-285">Restoring a game stored on the server.</span></span>
    * <span data-ttu-id="970de-286">Zeichnen des Spielbretts und der Karten basierend auf der Benutzerauswahl.</span><span class="sxs-lookup"><span data-stu-id="970de-286">Drawing the game board and cards based on user selection.</span></span>
    * <span data-ttu-id="970de-287">Umdrehen der Karten.</span><span class="sxs-lookup"><span data-stu-id="970de-287">Flipping the cards.</span></span>

2. <span data-ttu-id="970de-288">Beginnen wir in script.js mit dem Ändern der `newGame()`-Funktion.</span><span class="sxs-lookup"><span data-stu-id="970de-288">In script.js, let's start by modifying the `newGame()` function.</span></span> <span data-ttu-id="970de-289">Diese Funktion:</span><span class="sxs-lookup"><span data-stu-id="970de-289">This function:</span></span>

    * <span data-ttu-id="970de-290">Bearbeitet die Größe der Spielauswahl des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="970de-290">Handles the size of the game selection from the user.</span></span>
    * <span data-ttu-id="970de-291">Ruft die [Gameboard-Array](#part-i-build-a-rest-api-backend) vom Server auf.</span><span class="sxs-lookup"><span data-stu-id="970de-291">Fetches the [gameboard array](#part-i-build-a-rest-api-backend) from the server.</span></span>
    * <span data-ttu-id="970de-292">Ruft die `drawGameBoard()` -Funktion auf, um das Spielbrett auf dem Bildschirm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="970de-292">Calls the `drawGameBoard()` function to place the game board to the screen.</span></span>

    <span data-ttu-id="970de-293">Fügen Sie folgenden Code in `newGame()` nach dem Kommentar `// Add code from Part 2.2 here` ein.</span><span class="sxs-lookup"><span data-stu-id="970de-293">Add the following code inside of `newGame()` after the `// Add code from Part 2.2 here` comment.</span></span>

    ``` javascript
    // extract game size selection from user
    var size = $("#selectGameSize").val();

    // parse game size value
    size = parseInt(size, 10);
    ```

    <span data-ttu-id="970de-294">Dieser Code ruft den Wert aus dem Dropdownmenü mit `id="selectGameSize"` (was wir später noch erstellen) ab und speichert ihn in einer variablen (`size`).</span><span class="sxs-lookup"><span data-stu-id="970de-294">This code retrieves the value from the dropdown menu with `id="selectGameSize"` (which we will create later) and stores it in a variable (`size`).</span></span>  <span data-ttu-id="970de-295">Wir verwenden die [`parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)-Funktion zum Analysieren des String-Werts aus der Dropdownliste, um eine ganze Zahl zurückzugeben, damit wir die `size` des angeforderten Spiels an den Server übermitteln können.</span><span class="sxs-lookup"><span data-stu-id="970de-295">We use the [`parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) function to parse the string value from the dropdown to return an integer, so we can pass the `size` of the requested game board to the server.</span></span> 

    <span data-ttu-id="970de-296">Wir verwenden die [`/new`](#part-i-build-a-rest-api-backend)-Methode, die in Teil I dieses Lernprogramms erstellt wurde, um die ausgewählte Größe des Spiels an den Server zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="970de-296">We use the [`/new`](#part-i-build-a-rest-api-backend) method created in Part I of this tutorial to post the chosen size of the game board to the server.</span></span> <span data-ttu-id="970de-297">Die Methode gibt ein einzelnes JSON-Array von Karten `true/false`-Werte zurück, die angeben, ob die Karten zugeordnet wurden.</span><span class="sxs-lookup"><span data-stu-id="970de-297">The method returns a single JSON array of cards and `true/false` values indicating whether the cards have been matched.</span></span> 

3. <span data-ttu-id="970de-298">Füllen Sie als Nächstes die `restoreGame()`-Funktion aus, die das zuletzt gespielte Spiel wiederherstellt.</span><span class="sxs-lookup"><span data-stu-id="970de-298">Next, fill in the `restoreGame()` function that restores the last game played.</span></span> <span data-ttu-id="970de-299">Der Einfachheit halber lädt die App immer das zuletzt gespielte Spiel.</span><span class="sxs-lookup"><span data-stu-id="970de-299">For simplicity's sake, the app always loads the last game played.</span></span> <span data-ttu-id="970de-300">Wenn kein Spiel auf dem Server gespeichert ist, verwenden Sie das Dropdown-Menü, um ein neues Spiel zu starten.</span><span class="sxs-lookup"><span data-stu-id="970de-300">If there is not a game stored on the server, use the drop-down menu to start a new game.</span></span> 

    <span data-ttu-id="970de-301">Kopieren und fügen Sie diesen Code in `restoreGame()` ein.</span><span class="sxs-lookup"><span data-stu-id="970de-301">Copy and paste this code into `restoreGame()`.</span></span>

   ``` javascript 
   // reset the game
   gameBoardSize = 0;
   cardsFlipped = 0;

   // fetch the game state from the server 
   $.get("http://localhost:8000/game", function (response) {
       // store game board size
       gameBoardSize = response.length;

       // draw the game board
       drawGameBoard(response);
   });
   ```

    <span data-ttu-id="970de-302">Das Spiel wird nun den Spielezustand vom Server abrufen.</span><span class="sxs-lookup"><span data-stu-id="970de-302">The game will now fetch the game state from the server.</span></span> <span data-ttu-id="970de-303">Weitere Informationen zur [`/game`](#part-i-build-a-rest-api-backend)-Methode für diesen Schritt finden Sie in Teil I des Lernprogramms.</span><span class="sxs-lookup"><span data-stu-id="970de-303">For more information about the [`/game`](#part-i-build-a-rest-api-backend) method being used in this step, see Part I of this tutorial.</span></span> <span data-ttu-id="970de-304">Bei Verwendung von Azure (oder einem anderen Dienst) zum Hosten der Back-End-API, ersetzen Sie die *Localhost*-Adresse oben mit der Produktions-URL-Adresse.</span><span class="sxs-lookup"><span data-stu-id="970de-304">If you are using Azure (or another service) to host the backend API, replace the *localhost* address above with your production URL.</span></span>

4. <span data-ttu-id="970de-305">Jetzt erstellen wir die `drawGameBoard()`-Funktion.</span><span class="sxs-lookup"><span data-stu-id="970de-305">Now we want to create the `drawGameBoard()` function.</span></span>  <span data-ttu-id="970de-306">Diese Funktion:</span><span class="sxs-lookup"><span data-stu-id="970de-306">This function:</span></span>

    * <span data-ttu-id="970de-307">Erfasst die Größe des Spiels und wendet bestimmte CSS-Formatvorlagen an.</span><span class="sxs-lookup"><span data-stu-id="970de-307">Detects the size of the game and applies specific CSS styles.</span></span>
    * <span data-ttu-id="970de-308">Generiert die Karten im HTML-Code.</span><span class="sxs-lookup"><span data-stu-id="970de-308">Generates the cards in HTML.</span></span>
    * <span data-ttu-id="970de-309">Fügt die Karten und der Seite hinzu.</span><span class="sxs-lookup"><span data-stu-id="970de-309">Adds the cards to the page.</span></span>

    <span data-ttu-id="970de-310">Kopieren und fügen Sie diesen Code in die `drawGameBoard()`-Funktion in *scripts.js* ein:</span><span class="sxs-lookup"><span data-stu-id="970de-310">Copy and paste this code into the `drawGameBoard()` function in *scripts.js*:</span></span>

    ``` javascript
    // create output
    var output = "";
    // detect board size CSS class
    var css = "";
    switch (board.length / 4) {
        case 1:
            css = "rows1";
            break;
        case 2:
            css = "rows2";
            break;
        case 3:
            css = "rows3";
            break;
        case 4:
            css = "rows4";
            break;   
    }
    // generate HTML for each card and append to the output
    for (var i = 0; i < board.length; i++) {
        if (board[i].cleared == "true") {
            // if the card has been cleared apply the .flip class
            output += "<div class=\"flipContainer col-xs-3 " + css + "\"><div class=\"cards flip matched\" id=\"" + i + "\" onClick=\"flipCard(this)\">\
                <div class=\"front\"><span class=\"glyphicon glyphicon-question-sign\"></span></div>\
                <div class=\"back\">" + lookUpGlyphicon(board[i].value) + "</div>\
                </div></div>";
        } else {
            output += "<div class=\"flipContainer col-xs-3 " + css + "\"><div class=\"cards\" id=\"" + i + "\" onClick=\"flipCard(this)\">\
                <div class=\"front\"><span class=\"glyphicon glyphicon-question-sign\"></span></div>\
                <div class=\"back\"></div>\
                </div></div>";
        }
    }
    // place the output on the page
    $("#game-board").html(output);
    ```

5. <span data-ttu-id="970de-311">Als Nächstes müssen wir die `flipCard()`-Funktion abschließen.</span><span class="sxs-lookup"><span data-stu-id="970de-311">Next, we need to complete the `flipCard()` function.</span></span>  <span data-ttu-id="970de-312">Diese Funktion bearbeitet den Großteil der Spiellogik, einschließlich der Werte der ausgewählten Karten aus dem Server, anhand der [`/guess`](#part-i-build-a-rest-api-backend) -Methode, die in Teil I des Lernprogramms entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="970de-312">This function handles the majority of the game logic, including getting the values of the selected cards from the server by using the [`/guess`](#part-i-build-a-rest-api-backend) method developed in Part I of the tutorial.</span></span> <span data-ttu-id="970de-313">Vergessen Sie nicht, die *Localhost*-Adresse mit Ihrer Produktions-URL-Adresse zu ersetzen, wenn Sie das-REST-API-Back-End über die Cloud hosten.</span><span class="sxs-lookup"><span data-stu-id="970de-313">Don't forget to replace the *localhost* address with your production URL if you are cloud hosting the REST API backend.</span></span>

    <span data-ttu-id="970de-314">Entfernen Sie in der `flipCard()`-Funktion das Kommentar zu diesem Code:</span><span class="sxs-lookup"><span data-stu-id="970de-314">In the `flipCard()` function, uncomment this code:</span></span>

    ``` javascript
    // post this guess to the server and get this card's value
    $.ajax({
        url: "http://localhost:8000/guess?card=" + selectedCards[0],
        type: 'PUT',
        success: function (response) {
            // display first card value
            $("#" + selectedCards[0] + " .back").html(lookUpGlyphicon(response[0].value));

            // store the first card value
            selectedCardsValues.push(response[0].value);
        }
    });
    ```

> [!TIP] 
> <span data-ttu-id="970de-315">Wenn Sie Visual Studio Code verwenden, wählen Sie alle Codezeilen aus, bei denen Sie die Kommentare löschen möchten, und drücken Sie STRG+K, U.</span><span class="sxs-lookup"><span data-stu-id="970de-315">If you're using Visual Studio Code, select all the lines of code you wish to uncomment, and press Crtl + K, U</span></span>

<span data-ttu-id="970de-316">Hier verwenden wir [`jQuery.ajax()`](http://api.jquery.com/jQuery.ajax/) und die **PLATZIEREN**[`/guess`](#part-i-build-a-rest-api-backend)-Methode, die wir in Teil I erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="970de-316">Here we use [`jQuery.ajax()`](http://api.jquery.com/jQuery.ajax/) and the **PUT** [`/guess`](#part-i-build-a-rest-api-backend) method created in Part I.</span></span> 

<span data-ttu-id="970de-317">Dieser Code wird in der folgenden Reihenfolge ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="970de-317">This code executes in the following order.</span></span>

* <span data-ttu-id="970de-318">Die `id` der ersten vom Benutzer ausgewählten Karte wird als erster Wert in das SelectedCards[]-Array hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="970de-318">The `id` of the first card the user selected is added as the first value to the selectedCards[] array:</span></span> `selectedCards[0]` 
* <span data-ttu-id="970de-319">Der Wert (`id`) in `selectedCards[0]` wird an den Server anhand der [`/guess`](#part-i-build-a-rest-api-backend)-Methode gesendet.</span><span class="sxs-lookup"><span data-stu-id="970de-319">The value (`id`) in `selectedCards[0]` is posted to the server using the [`/guess`](#part-i-build-a-rest-api-backend) method</span></span>
* <span data-ttu-id="970de-320">Der Server antwortet mit dem `value` der Karte (eine ganze Zahl).</span><span class="sxs-lookup"><span data-stu-id="970de-320">The server responds with the `value` of that card (an integer)</span></span>
* <span data-ttu-id="970de-321">Ein [Bootstrap Glyphicon](http://getbootstrap.com/components/) wird an die Rückseite der Karte hinzugefügt, deren `id` folgendermaßen lautet.</span><span class="sxs-lookup"><span data-stu-id="970de-321">A [Bootstrap glyphicon](http://getbootstrap.com/components/) is added to the back of the card whose `id` is</span></span> `selectedCards[0]`
* <span data-ttu-id="970de-322">Der `value` der ersten Karte (vom Server) ist im `selectedCardsValues[]`-Array: `selectedCardsValues[0]` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="970de-322">The first card's `value` (from the server) is stored in the `selectedCardsValues[]` array: `selectedCardsValues[0]`.</span></span> 

<span data-ttu-id="970de-323">Der zweite Versuch des Benutzers folgt derselben Logik.</span><span class="sxs-lookup"><span data-stu-id="970de-323">The user's second guess follows the same logic.</span></span> <span data-ttu-id="970de-324">Wenn die vom Benutzer ausgewählten Karten die gleichen IDs besitzen (z.B. `selectedCards[0] == selectedCards[1]`), stimmen die Karten überein!</span><span class="sxs-lookup"><span data-stu-id="970de-324">If the cards that the user selected have the same IDs, (for example, `selectedCards[0] == selectedCards[1]`), the cards are a match!</span></span> <span data-ttu-id="970de-325">Die CSS-Klasse `.matched` wird den übereinstimmenden Karten hinzugefügt (wodurch sie grün werden), und die Karten bleiben aufgedeckt.</span><span class="sxs-lookup"><span data-stu-id="970de-325">The CSS class `.matched` is added to the matched cards (turning them green) and the cards remained flipped.</span></span>

<span data-ttu-id="970de-326">Nun müssen wir Logik hinzufügen, um zu überprüfen, ob der Benutzer alle übereinstimmenden Karten gefunden und das Spiel gewonnen hat.</span><span class="sxs-lookup"><span data-stu-id="970de-326">Now we need to add logic to check whether the user matched all of the cards and won the game.</span></span> <span data-ttu-id="970de-327">Fügen Sie in der `flipCard()`-Funktion die folgenden Codezeilen unter dem `//check if the user won the game`-Kommentar hinzu.</span><span class="sxs-lookup"><span data-stu-id="970de-327">Inside of the `flipCard()` function, add the following lines of code under the `//check if the user won the game` comment.</span></span> 

``` javascript
if (cardsFlipped == gameBoardSize) {
    setTimeout(function () {
        output = "<div id=\"playAgain\"><p>You Win!</p><input type=\"button\" onClick=\"location.reload()\" value=\"Play Again\" class=\"btn\" /></div>";
        $("#game-board").html(output);
    }, 1000);
}   
```

<span data-ttu-id="970de-328">Wenn die Anzahl der aufgedeckten Karten die Größe des Spielbretts entspricht (z.B. `cardsFlipped == gameBoardSize`), gibt keine weiteren Karten, die aufgedeckt werden können, und der Benutzer hat das Spiel gewonnen.</span><span class="sxs-lookup"><span data-stu-id="970de-328">If the number of cards flipped matches the size of the game board (for example, `cardsFlipped == gameBoardSize`), there are no more cards to flip and the user has won the game.</span></span> <span data-ttu-id="970de-329">Wir fügen einige einfache HTML-Codezeilen zur `div` hinzu mit `id="game-board"`, damit der Benutzer weiß, dass er gewonnen hat und erneut spielen kann.</span><span class="sxs-lookup"><span data-stu-id="970de-329">We'll add some simple HTML to the `div` with `id="game-board"` to let the user know they won and can play again.</span></span>  

### <a name="3-create-the-user-interface"></a><span data-ttu-id="970de-330">3. Erstellen einer Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="970de-330">3. Create the user interface</span></span> 
<span data-ttu-id="970de-331">Jetzt sehen wir uns diesen Code in Aktion an, indem wir die Benutzeroberfläche erstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-331">Now let's see all this code in action by creating the user interface.</span></span> <span data-ttu-id="970de-332">In diesem Lernprogramm verwenden wir das Vorlagenmodul [Pug](https://pugjs.org/) (formell Jade).</span><span class="sxs-lookup"><span data-stu-id="970de-332">In this tutorial, we use the templating engine [Pug](https://pugjs.org/) (formally Jade).</span></span>  <span data-ttu-id="970de-333">*Pug* ist eine saubere Syntax zum Schreiben von HTML-Code, die auf Leerzeichen achtet.</span><span class="sxs-lookup"><span data-stu-id="970de-333">*Pug* is clean, whitespace-sensitive syntax for writing HTML.</span></span> <span data-ttu-id="970de-334">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="970de-334">Here's an example.</span></span> 

```
body
    h1 Memory Game
    #container
        p We love tutorials!
```

<span data-ttu-id="970de-335">wird</span><span class="sxs-lookup"><span data-stu-id="970de-335">becomes</span></span>

``` html
<body>
    <h1>Memory Game</h1>
    <div id="container">
        <p>We love tutorials!</p>
    </div>
</body>
```


1. <span data-ttu-id="970de-336">Ersetzen Sie die Datei layout.pug in memory\views mit der bereitgestellten Datei layout.pug-Datei im Ordner „Start”.</span><span class="sxs-lookup"><span data-stu-id="970de-336">Replace the layout.pug file in memory\views with the provided layout.pug file in the Start folder.</span></span> <span data-ttu-id="970de-337">In layout.pug sehen Sie Links zu:</span><span class="sxs-lookup"><span data-stu-id="970de-337">Inside of layout.pug, you'll see links to:</span></span>

    * <span data-ttu-id="970de-338">Bootstrap</span><span class="sxs-lookup"><span data-stu-id="970de-338">Bootstrap</span></span>
    * <span data-ttu-id="970de-339">jQuery</span><span class="sxs-lookup"><span data-stu-id="970de-339">jQuery</span></span>
    * <span data-ttu-id="970de-340">Eine benutzerdefinierte CSS-Datei</span><span class="sxs-lookup"><span data-stu-id="970de-340">A custom CSS file</span></span>
    * <span data-ttu-id="970de-341">Die JavaScript-Datei, die wir gerade geändert haben</span><span class="sxs-lookup"><span data-stu-id="970de-341">The JavaScript file we just finished modifying</span></span>

2. <span data-ttu-id="970de-342">Öffnen Sie die Datei mit dem Namen index.pug im Verzeichnis memory\views.</span><span class="sxs-lookup"><span data-stu-id="970de-342">Open the file named index.pug in the directory memory\views.</span></span>
<span data-ttu-id="970de-343">Diese Datei erweitert die Datei layout.pug und wird unser Spiel rendern.</span><span class="sxs-lookup"><span data-stu-id="970de-343">This file extends the layout.pug file and will render our game.</span></span> <span data-ttu-id="970de-344">Fügen Sie in layout.pug die folgenden Codezeilen ein:</span><span class="sxs-lookup"><span data-stu-id="970de-344">Inside of layout.pug, paste the following lines of code:</span></span>

    ```
    extends layout
    block content  
        div
            form(method="GET")
            select(id="selectGameSize" class="form-control" onchange="newGame()")
                option(value="0") New Game
                option(value="2") 2 Matches
                option(value="4") 4 Matches
                option(value="6") 6 Matches
                option(value="8") 8 Matches         
            #game-board
                script restoreGame();
    ```

> [!TIP] 
> <span data-ttu-id="970de-345">Denken Sie daran: Pug beachtet Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="970de-345">Remember: Pug is whitespace sensitive.</span></span> <span data-ttu-id="970de-346">Stellen Sie sicher, dass alle Ihre Einzüge richtig sind!</span><span class="sxs-lookup"><span data-stu-id="970de-346">Make sure all of your indentations are correct!</span></span>

### <a name="4-use-bootstraps-grid-system-to-create-a-responsive-layout"></a><span data-ttu-id="970de-347">4. Verwenden Sie das Rastersystem von Bootstrap, um ein dynamisches Layout zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-347">4. Use Bootstrap's grid system to create a responsive layout</span></span>
<span data-ttu-id="970de-348">Das [Rastersystem](http://getbootstrap.com/css/#grid) von Bootstrap ist ein dynamisches Rastersystem, das ein Raster beim Ändern eines Geräte-Viewports skaliert.</span><span class="sxs-lookup"><span data-stu-id="970de-348">Bootstrap's [grid system](http://getbootstrap.com/css/#grid) is a fluid grid system that scales a grid as a device's viewport changes.</span></span> <span data-ttu-id="970de-349">Die Karten in diesem Spiel verwenden die vordefinierten Rastersystemklassen von Bootstrap für das Layout, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="970de-349">The cards in this game use Bootstrap's predefined grid system classes for the layout, including:</span></span>
* `.container-fluid`<span data-ttu-id="970de-350">: Gibt den dynamischen Container für das Raster an</span><span class="sxs-lookup"><span data-stu-id="970de-350">: specifies the fluid container for the grid</span></span>
* `.row-fluid`<span data-ttu-id="970de-351">: Gibt die dynamischen Zeilen an</span><span class="sxs-lookup"><span data-stu-id="970de-351">: specifies the fluid rows</span></span>
* `.col-xs-3`<span data-ttu-id="970de-352">: Gibt die Anzahl von Spalten an</span><span class="sxs-lookup"><span data-stu-id="970de-352">: specifies the number of columns</span></span>

<span data-ttu-id="970de-353">Mit dem Rastersystem von Bootstrap kann ein Rastersystem in eine vertikalen Spalte zusammengeklappt werden, wie bei einem Navigationsmenü eines mobilen Geräts.</span><span class="sxs-lookup"><span data-stu-id="970de-353">Bootstrap's grid system allows a grid system to collapse into one vertical column, like you would see on a navigation menu on a mobile device.</span></span>  <span data-ttu-id="970de-354">Da wir jedoch bei unserem Spiel immer Spalten haben sollen, verwenden wir die vordefinierte Klasse `.col-xs-3`, die jederzeit für ein horizontales Raster sorgt.</span><span class="sxs-lookup"><span data-stu-id="970de-354">However, because we want our game always to have columns, we use the predefined class `.col-xs-3`, which keeps the grid horizontal at all times.</span></span> 

<span data-ttu-id="970de-355">Das Rastersystem ermöglicht bis zu 12 Spalten.</span><span class="sxs-lookup"><span data-stu-id="970de-355">The grid system allows up to 12 columns.</span></span> <span data-ttu-id="970de-356">Da wir nur 4 Spalten in unserem Spiel haben möchten, verwenden wir die Klasse `.col-xs-3`.</span><span class="sxs-lookup"><span data-stu-id="970de-356">Since we only want 4 columns in our game, we use the class `.col-xs-3`.</span></span> <span data-ttu-id="970de-357">Diese Klasse gibt an, dass die gewünschten Spalten eine Breite von 3 der 12 bereits erwähnten Spalten umfassen.</span><span class="sxs-lookup"><span data-stu-id="970de-357">This class specifies that we need each of our columns to span the width of 3 of the 12 available columns mentioned before.</span></span> <span data-ttu-id="970de-358">Diese Abbildung zeigt ein Raster mit 12 Spalten und ein Raster mit 4 Spalten, wie es in diesem Spiel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="970de-358">This image shows a 12-column grid and a 4-column grid, like the one used in this game.</span></span>

![Bootstrap-Raster mit 12 Spalten und 4 Zeilen](./images/grid.png)

1. <span data-ttu-id="970de-360">Öffnen Sie scripts.js und suchen Sie die `drawGameBoard()`-Funktion.</span><span class="sxs-lookup"><span data-stu-id="970de-360">Open scripts.js and find the `drawGameBoard()` function.</span></span>  <span data-ttu-id="970de-361">Können Sie im Codeblock, in dem wir den HTML-Code für jede Karte generieren, das `div`-Element mit `class="col-xs-3"` erkennen?</span><span class="sxs-lookup"><span data-stu-id="970de-361">In the block of code where we generate the HTML for each card, can you spot the `div` element with `class="col-xs-3"`?</span></span> 

2. <span data-ttu-id="970de-362">Fügen Sie in Index.pug die zuvor erwähnten vordefinierten Bootstrap-Klassen hinzu, um unser dynamisches Layout zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-362">Inside of index.pug, let's add the predefined Bootstrap classes mentioned previously to create our fluid layout.</span></span>  <span data-ttu-id="970de-363">Ändern Sie index.pug folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="970de-363">Change index.pug to the following.</span></span>

    ```
    extends layout

    block content   

        .container-fluid
            form(method="GET")
            select(id="selectGameSize" class="form-control" onchange="newGame()")
                option(value="0") New Game
                option(value="2") 2 Matches
                option(value="4") 4 Matches
                option(value="6") 6 Matches
                option(value="8") 8 Matches         
            #game-board.row-fluid 
                script restoreGame();
    ```

### <a name="5-add-a-card-flip-animation-with-css-transforms"></a><span data-ttu-id="970de-364">5. Fügen Sie eine Karten-Flip-Animation mit CSS-Transformationen hinzu</span><span class="sxs-lookup"><span data-stu-id="970de-364">5. Add a card-flip animation with CSS Transforms</span></span>
<span data-ttu-id="970de-365">Ersetzen Sie die Datei style.css im Verzeichnis memory\public\stylesheets mit der Datei style.css aus dem Ordner „Start”.</span><span class="sxs-lookup"><span data-stu-id="970de-365">Replace the style.css file in memory\public\stylesheets with the style.css file from the Start folder.</span></span>

<span data-ttu-id="970de-366">Das Hinzufügen einer Flip-Bewegung mit [CSS-Transformationen](https://docs.microsoft.com/en-us/microsoft-edge/dev-guide/css/transforms) verleiht den Karten eine realistische 3D-Flip-Bewegung.</span><span class="sxs-lookup"><span data-stu-id="970de-366">Adding a flip motion using [CSS Transforms](https://docs.microsoft.com/en-us/microsoft-edge/dev-guide/css/transforms) gives the cards a realistic, 3D flipping motion.</span></span> <span data-ttu-id="970de-367">Die Karten im Spiel werden anhand der folgenden HTML-Struktur erstellt und dem Spielbrett programmgesteuert hinzugefügt (in der zuvor gezeigten `drawGameBoard()`-Funktion).</span><span class="sxs-lookup"><span data-stu-id="970de-367">The cards in the game are created by using the following HTML structure and programmatically added to the game board (in the `drawGameBoard()` function shown previously).</span></span>

``` html
<div class="flipContainer">
    <div class="cards">
        <div class="front"></div>
        <div class="back"></div>
    </div>
</div>
```

1. <span data-ttu-id="970de-368">Geben Sie dem übergeordneten Container der Animation zunächst [Perspektive](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) (`.flipContainer`).</span><span class="sxs-lookup"><span data-stu-id="970de-368">To start, give [perspective](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) to the parent container of the animation (`.flipContainer`).</span></span>  <span data-ttu-id="970de-369">Dadurch entsteht für seine untergeordneten Elemente die Illusion von Tiefe: je höher der Wert, desto weiter Weg erscheint dem Benutzer das Element.</span><span class="sxs-lookup"><span data-stu-id="970de-369">This gives the illusion of depth for its child elements: the higher the value, the farther away from the user the element will appear.</span></span> <span data-ttu-id="970de-370">Nun fügen wir in style.css die folgende Perspektive der `.flipContainer`-Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="970de-370">Let's add the following perspective to the `.flipContainer` class in style.css.</span></span>

    ``` css
    perspective: 1000px; 
    ```

2. <span data-ttu-id="970de-371">Fügen Sie jetzt die folgenden Eigenschaften der `.cards`-Klasse in style.css hinzu.</span><span class="sxs-lookup"><span data-stu-id="970de-371">Now add the following properties to the `.cards` class in style.css.</span></span> <span data-ttu-id="970de-372">Das `.cards` `div` ist das Element, das die Flip-Animation tatsächlich ausführt und entweder die Vorder- oder Rückseite der Karte aufdeckt.</span><span class="sxs-lookup"><span data-stu-id="970de-372">The `.cards` `div` is the element that will actually be doing the flipping animation, showing either the front or the back of the card.</span></span> 

    ``` css
    transform-style: preserve-3d;
    transition-duration: 1s;
    ```

    <span data-ttu-id="970de-373">Die [`transform-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-style)-Eigenschaft erstellt ein 3D-Rendering-Kontext, und die untergeordneten Elemente der `.cards`-Klasse (`.front` und `.back`) sind Mitglieder des 3D-Raums.</span><span class="sxs-lookup"><span data-stu-id="970de-373">The [`transform-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-style) property establishes a 3D-rendering context, and the children of the `.cards` class (`.front` and `.back` are members of the 3D space.</span></span> <span data-ttu-id="970de-374">Das Hinzufügen der [`transition-duration`](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-duration) -Eigenschaft gibt die Anzahl der Sekunden für die Ausführung der Animation an.</span><span class="sxs-lookup"><span data-stu-id="970de-374">Adding the [`transition-duration`](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-duration) property specifies the number of seconds for the animation to finish.</span></span> 

3.  <span data-ttu-id="970de-375">Mit der [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) -Eigenschaft können wir die Karte um die Y-Achse drehen.</span><span class="sxs-lookup"><span data-stu-id="970de-375">Using the [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) property, we can rotate the card around the Y-axis.</span></span>  <span data-ttu-id="970de-376">Fügen Sie den `cards.flip` den folgenden CSS-Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="970de-376">Add the following CSS to `cards.flip`.</span></span>

    ``` css
    transform: rotateY(180deg);
    ```

    <span data-ttu-id="970de-377">Der in `cards.flip` definierte Stil kann in der `flipCard`-Funktion mit [`.toggleClass()`](http://api.jquery.com/toggleClass/) ein- und ausgeschaltet werden.</span><span class="sxs-lookup"><span data-stu-id="970de-377">The style defined in `cards.flip` is toggled on and off in the `flipCard` function by using [`.toggleClass()`](http://api.jquery.com/toggleClass/).</span></span> 

    ``` javascript
    $(card).toggleClass("flip");
    ```

    <span data-ttu-id="970de-378">Wenn ein Benutzer nun auf eine Karte klickt, wird die Karte um 180Grad gedreht.</span><span class="sxs-lookup"><span data-stu-id="970de-378">Now when a user clicks on a card, the card is rotated 180 degrees.</span></span>

### <a name="6-test-and-play"></a><span data-ttu-id="970de-379">6. Testen und spielen</span><span class="sxs-lookup"><span data-stu-id="970de-379">6. Test and play</span></span>
<span data-ttu-id="970de-380">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="970de-380">Congratulations!</span></span> <span data-ttu-id="970de-381">Sie haben die Web-App erfolgreich erstellt!</span><span class="sxs-lookup"><span data-stu-id="970de-381">You've finished creating the web app!</span></span> <span data-ttu-id="970de-382">Testen wir sie.</span><span class="sxs-lookup"><span data-stu-id="970de-382">Let's test it.</span></span> 

1. <span data-ttu-id="970de-383">Öffnen Sie eine Eingabeaufforderung im Arbeitsspeicherverzeichnis, und geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="970de-383">Open a command prompt in your memory directory and enter the following command:</span></span> `npm start`

2. <span data-ttu-id="970de-384">Rufen Sie in Ihrem Browser [http://localhost:3000/](http://localhost:3000/) auf und spielen Sie ein Spiel!</span><span class="sxs-lookup"><span data-stu-id="970de-384">In your browser, go to [http://localhost:3000/](http://localhost:3000/) and play a game!</span></span>

3. <span data-ttu-id="970de-385">Wenn Fehler auftreten, können Sie die Node.js-Debugtools von Visual Studio Code durch Drücken von F5 auf der Tastatur und Eingeben von `Node.js` verwenden.</span><span class="sxs-lookup"><span data-stu-id="970de-385">If you encounter any errors, you can use Visual Studio Code's Node.js debugging tools by pressing F5 on your keyboard and typing `Node.js`.</span></span> <span data-ttu-id="970de-386">Weitere Informationen zum Debuggen in Visual Studio Code finden Sie in diesem [Artikel](http://code.visualstudio.com/docs/editor/debugging#_launch-configurations).</span><span class="sxs-lookup"><span data-stu-id="970de-386">For more information about debugging in Visual Studio Code, check out this [article](http://code.visualstudio.com/docs/editor/debugging#_launch-configurations).</span></span> 

    <span data-ttu-id="970de-387">Sie können auch Ihren Code mit dem im letzten Ordner zur Verfügung gestellten Code vergleichen.</span><span class="sxs-lookup"><span data-stu-id="970de-387">You can also compare your code to the code provided in the Final folder.</span></span>

4. <span data-ttu-id="970de-388">Geben Sie zum Beenden des Spiels in das Eingabeaufforderungsfenster Folgendes ein: **STRG+C**, **Y**.</span><span class="sxs-lookup"><span data-stu-id="970de-388">To stop the game, in the command prompt type: **Ctrl + C**, **Y**.</span></span> 

### <a name="going-further"></a><span data-ttu-id="970de-389">Vertiefung</span><span class="sxs-lookup"><span data-stu-id="970de-389">Going further</span></span>

<span data-ttu-id="970de-390">Sie können jetzt Sie Ihre App in Azure (oder einen anderen Cloud-Hostingdienst) zum Testen auf verschiedenen Geräteformfaktoren, z.B. Mobile, Tablet und PC, bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="970de-390">You can now deploy your app to Azure (or any other cloud hosting service) for testing across different device form factors, such as mobile, tablet, and desktop.</span></span> <span data-ttu-id="970de-391">(Vergessen Sie nicht, Ihre App in verschiedenen Browsern zu testen!) Sobald Ihre App für die Produktion bereit ist, können Sie sie ganz einfach als eine *gehostete Web-App* (Hosted Web App, HWA) für die *Universelle Windows-Plattform* (UWP) verpacken und sie aus dem Microsoft Store verteilen.</span><span class="sxs-lookup"><span data-stu-id="970de-391">(Don't forgot to test across different browsers too!) Once your app is ready for production, you can easily package it as a *Hosted Web App* (HWA) for the *Universal Windows Platform* (UWP) and distribute it from the Microsoft Store.</span></span>

<span data-ttu-id="970de-392">Die grundlegenden Schritte für die Veröffentlichung auf dem Microsoft Store sind:</span><span class="sxs-lookup"><span data-stu-id="970de-392">The basic steps for publishing to the Microsoft Store are:</span></span>

 1. <span data-ttu-id="970de-393">Erstellen Sie ein Konto für [Windows-Entwickler](https://developer.microsoft.com/en-us/store/register).</span><span class="sxs-lookup"><span data-stu-id="970de-393">Create a [Windows Developer](https://developer.microsoft.com/en-us/store/register) account</span></span>
 2. <span data-ttu-id="970de-394">Verwenden Sie die [Prüfliste für die App-Übermittlung](https://docs.microsoft.com/en-us/windows/uwp/publish/app-submissions).</span><span class="sxs-lookup"><span data-stu-id="970de-394">Use the app submission [checklist](https://docs.microsoft.com/en-us/windows/uwp/publish/app-submissions)</span></span>
 3. <span data-ttu-id="970de-395">Reichen Sie Ihre App für die [Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process) ein.</span><span class="sxs-lookup"><span data-stu-id="970de-395">Submit your app for [certification](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process)</span></span>

<span data-ttu-id="970de-396">Hier sind einige nützliche Ressourcen für die weiterfühRendern Schritte:</span><span class="sxs-lookup"><span data-stu-id="970de-396">Here are some useful resources for going further:</span></span>

 - [<span data-ttu-id="970de-397">Stellen Sie Ihr App-Entwicklungsprojekt für Azure-Websites bereit.</span><span class="sxs-lookup"><span data-stu-id="970de-397">Deploy your application development project to Azure Websites</span></span>](https://docs.microsoft.com/azure/cosmos-db/documentdb-nodejs-application#_Toc395783182)

 - [<span data-ttu-id="970de-398">Konvertieren Ihrer Webanwendung in eine App für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="970de-398">Convert your web application to a Universal Windows Platform (UWP) app</span></span>](https://docs.microsoft.com/en-us/windows/uwp/porting/hwa-create-windows)

 - [<span data-ttu-id="970de-399">Veröffentlichen von Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="970de-399">Publish Windows apps</span></span>](https://developer.microsoft.com/en-us/store/publish-apps)
