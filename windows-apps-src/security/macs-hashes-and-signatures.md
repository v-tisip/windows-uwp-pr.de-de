---
title: MACs, Hashes und Signaturen
description: In diesem Thema wird erläutert, wie Nachrichtenauthentifizierungscodes (MACs), Hashes und Signaturen in UWP-Apps verwendet werden können, um die Manipulation von Nachrichten zu erkennen.
ms.assetid: E674312F-6678-44C5-91D9-B489F49C4D3C
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 6517241826d06b63fd88b45237552acffbdc62da
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7701604"
---
# <a name="macs-hashes-and-signatures"></a><span data-ttu-id="5eafa-104">MACs, Hashes und Signaturen</span><span class="sxs-lookup"><span data-stu-id="5eafa-104">MACs, hashes, and signatures</span></span>




<span data-ttu-id="5eafa-105">In diesem Thema wird erläutert, wie Nachrichtenauthentifizierungscodes (MACs), Hashes und Signaturen in UWP-Apps verwendet werden können, um die Manipulation von Nachrichten zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="5eafa-105">This article discusses how message authentication codes (MACs), hashes, and signatures can be used in Universal Windows Platform (UWP) apps to detect message tampering.</span></span>

## <a name="message-authentication-codes-macs"></a><span data-ttu-id="5eafa-106">Nachrichtenauthentifizierungscodes (MACs)</span><span class="sxs-lookup"><span data-stu-id="5eafa-106">Message authentication codes (MACs)</span></span>


<span data-ttu-id="5eafa-107">Die Verschlüsselung hilft dabei, nicht autorisierte Personen davon abzuhalten, eine Nachricht zu lesen, kann jedoch nichts dagegen ausrichten, wenn Personen die Nachricht manipulieren.</span><span class="sxs-lookup"><span data-stu-id="5eafa-107">Encryption helps prevent an unauthorized individual from reading a message, but it does not prevent that individual from tampering with the message.</span></span> <span data-ttu-id="5eafa-108">Eine so veränderte Nachricht kann Kosten verursachen, selbst wenn die Veränderung keinen echten Inhalt vermittelt.</span><span class="sxs-lookup"><span data-stu-id="5eafa-108">An altered message, even if the alteration results in nothing but nonsense, can have real costs.</span></span> <span data-ttu-id="5eafa-109">Ein Nachrichtenauthentifizierungscode (Message Authentication Code, MAC) kann die Manipulation von Nachrichten verhindern.</span><span class="sxs-lookup"><span data-stu-id="5eafa-109">A message authentication code (MAC) helps prevent message tampering.</span></span> <span data-ttu-id="5eafa-110">Nehmen wir folgendes Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5eafa-110">For example, consider the following scenario:</span></span>

-   <span data-ttu-id="5eafa-111">Sven und Andrea geben einander einen geheimen Schlüssel weiter und einigen sich darauf, die MAC-Funktion zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="5eafa-111">Bob and Alice share a secret key and agree on a MAC function to use.</span></span>
-   <span data-ttu-id="5eafa-112">Sven schreibt eine Nachricht und gibt sie zusammen mit dem geheimen Schlüssel in eine MAC-Funktion ein, um einen MAC-Wert zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5eafa-112">Bob creates a message and inputs the message and the secret key into a MAC function to retrieve a MAC value.</span></span>
-   <span data-ttu-id="5eafa-113">Sven sendet die (nicht verschlüsselte) Nachricht und den MAC-Wert über ein Netzwerk an Andrea.</span><span class="sxs-lookup"><span data-stu-id="5eafa-113">Bob sends the \[unencrypted\] message and the MAC value to Alice over a network.</span></span>
-   <span data-ttu-id="5eafa-114">Andrea gibt den geheimen Schlüssel und die Nachricht ebenfalls in eine MAC-Funktion ein.</span><span class="sxs-lookup"><span data-stu-id="5eafa-114">Alice uses the secret key and the message as input to the MAC function.</span></span> <span data-ttu-id="5eafa-115">Sie vergleicht den MAC-Wert, den sie erhält, mit dem MAC-Wert, den Sie von Sven erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="5eafa-115">She compares the generated MAC value to the MAC value sent by Bob.</span></span> <span data-ttu-id="5eafa-116">Stimmen die Werte überein, wurde die Nachricht beim Verwenden nicht manipuliert.</span><span class="sxs-lookup"><span data-stu-id="5eafa-116">If they are the same, the message was not changed in transit.</span></span>

<span data-ttu-id="5eafa-117">Beachten Sie, dass Eve, die den Austausch zwischen Sven und Andrea heimlich mitverfolgt, die Nachricht so nicht manipulieren kann.</span><span class="sxs-lookup"><span data-stu-id="5eafa-117">Note that Eve, a third party eavesdropping on the conversation between Bob and Alice, cannot effectively manipulate the message.</span></span> <span data-ttu-id="5eafa-118">Eve hat keinen Zugriff auf den privaten Schlüssel und kann daher keinen MAC-Wert generieren, der die manipulierte Nachricht bei Andrea als unverändert erscheinen lassen könnte.</span><span class="sxs-lookup"><span data-stu-id="5eafa-118">Eve does not have access to the private key and cannot, therefore, create a MAC value which would make the tampered message appear legitimate to Alice.</span></span>

<span data-ttu-id="5eafa-119">Die Erstellung eines MAC-Werts gewährleistet somit, dass die ursprüngliche Nachricht nicht geändert wurde. Zudem beweist der Einsatz eines freigegebenen geheimen Schlüssels, dass der Nachrichtenhash von jemandem signiert wurde, der Zugriff auf den privaten Schlüssel hatte.</span><span class="sxs-lookup"><span data-stu-id="5eafa-119">Creating a message authentication code ensures only that the original message was not altered and, by using a shared secret key, that the message hash was signed by someone with access to that private key.</span></span>

<span data-ttu-id="5eafa-120">Sie können [**MacAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241530) zur Enumerierung der verfügbaren MAC-Algorithmen und zur Generierung eines symmetrischen Schlüssels verwenden.</span><span class="sxs-lookup"><span data-stu-id="5eafa-120">You can use the [**MacAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241530) to enumerate the available MAC algorithms and generate a symmetric key.</span></span> <span data-ttu-id="5eafa-121">Die statischen Methoden der [**CryptographicEngine**](https://msdn.microsoft.com/library/windows/apps/br241490)-Klasse können zudem zur Durchführung der erforderlichen Verschlüsselung genutzt werden, durch den Sie den MAC-Wert erhalten.</span><span class="sxs-lookup"><span data-stu-id="5eafa-121">You can use static methods on the [**CryptographicEngine**](https://msdn.microsoft.com/library/windows/apps/br241490) class to perform the necessary encryption that creates the MAC value.</span></span>

<span data-ttu-id="5eafa-122">Digitale Signaturen von öffentlichen Schlüsseln sind das Äquivalent der Nachrichtenauthentifizierungscodes (MACs) von privaten Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="5eafa-122">Digital signatures are the public key equivalent of private key message authentication codes (MACs).</span></span> <span data-ttu-id="5eafa-123">Obwohl MACs private Schlüssel verwenden, um dem Nachrichtenempfänger zu ermöglichen, Nachrichten zu überprüfen und sicherzugehen, dass diese bei der Übertragung nicht verändert wurden, verwenden Signaturen ein Schlüsselpaar aus einem privaten und einem öffentlichen Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="5eafa-123">Although MACs use private keys to enable a message recipient to verify that a message has not been altered during transmission, signatures use a private/public key pair.</span></span>

<span data-ttu-id="5eafa-124">In diesem Beispielcode ist die Verwendung der [**MacAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241530)-Klasse zum Erstellen eines Nachrichtenauthentifizierungscodes mit Hash (Hashed Message Authentication Code, HMAC) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5eafa-124">This example code shows how to use the [**MacAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241530) class to create a hashed message authentication code (HMAC).</span></span>

```cs
using Windows.Security.Cryptography;
using Windows.Security.Cryptography.Core;
using Windows.Storage.Streams;

namespace SampleMacAlgorithmProvider
{
    sealed partial class MacAlgProviderApp : Application
    {
        public MacAlgProviderApp()
        {
            // Initialize the application.
            this.InitializeComponent();

            // Initialize the hashing process.
            String strMsg = "This is a message to be authenticated";
            String strAlgName = MacAlgorithmNames.HmacSha384;
            IBuffer buffMsg;
            CryptographicKey hmacKey;
            IBuffer buffHMAC;

            // Create a hashed message authentication code (HMAC)
            this.CreateHMAC(
                strMsg,
                strAlgName,
                out buffMsg,
                out hmacKey,
                out buffHMAC);

            // Verify the HMAC.
            this.VerifyHMAC(
                buffMsg,
                hmacKey,
                buffHMAC);
        }

        void CreateHMAC(
            String strMsg,
            String strAlgName,
            out IBuffer buffMsg,
            out CryptographicKey hmacKey,
            out IBuffer buffHMAC)
        {
            // Create a MacAlgorithmProvider object for the specified algorithm.
            MacAlgorithmProvider objMacProv = MacAlgorithmProvider.OpenAlgorithm(strAlgName);

            // Demonstrate how to retrieve the name of the algorithm used.
            String strNameUsed = objMacProv.AlgorithmName;

            // Create a buffer that contains the message to be signed.
            BinaryStringEncoding encoding = BinaryStringEncoding.Utf8;
            buffMsg = CryptographicBuffer.ConvertStringToBinary(strMsg, encoding);

            // Create a key to be signed with the message.
            IBuffer buffKeyMaterial = CryptographicBuffer.GenerateRandom(objMacProv.MacLength);
            hmacKey = objMacProv.CreateKey(buffKeyMaterial);

            // Sign the key and message together.
            buffHMAC = CryptographicEngine.Sign(hmacKey, buffMsg);

            // Verify that the HMAC length is correct for the selected algorithm
            if (buffHMAC.Length != objMacProv.MacLength)
            {
                throw new Exception("Error computing digest");
            }
         }

        public void VerifyHMAC(
            IBuffer buffMsg,
            CryptographicKey hmacKey,
            IBuffer buffHMAC)
        {
            // The input key must be securely shared between the sender of the HMAC and 
            // the recipient. The recipient uses the CryptographicEngine.VerifySignature() 
            // method as follows to verify that the message has not been altered in transit.
            Boolean IsAuthenticated = CryptographicEngine.VerifySignature(hmacKey, buffMsg, buffHMAC);
            if (!IsAuthenticated)
            {
                throw new Exception("The message cannot be verified.");
            }
        }
    }
}
```

## <a name="hashes"></a><span data-ttu-id="5eafa-125">Hashes</span><span class="sxs-lookup"><span data-stu-id="5eafa-125">Hashes</span></span>


<span data-ttu-id="5eafa-126">Eine kryptografische Hashfunktion gibt für einen an sie übergebenen Datenblock beliebiger Länge eine Bitzeichenfolge fester Größe zurück.</span><span class="sxs-lookup"><span data-stu-id="5eafa-126">A cryptographic hash function takes an arbitrarily long block of data and returns a fixed-size bit string.</span></span> <span data-ttu-id="5eafa-127">Hashfunktionen werden normalerweise zum Signieren von Daten verwendet.</span><span class="sxs-lookup"><span data-stu-id="5eafa-127">Hash functions are typically used when signing data.</span></span> <span data-ttu-id="5eafa-128">Da die meisten Signaturvorgänge für öffentliche Schlüssel rechtenintensiv sind, ist das Signieren eines Nachrichtenhashes in der Regel effizienter als das Signieren der ursprünglichen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="5eafa-128">Because most public key signature operations are computationally intensive, it is typically more efficient to sign (encrypt) a message hash than it is to sign the original message.</span></span> <span data-ttu-id="5eafa-129">Im folgenden Verfahren wird ein gängiges Szenario vorgestellt, das für diese Zwecke aber vereinfacht wurde:</span><span class="sxs-lookup"><span data-stu-id="5eafa-129">The following procedure represents a common, albeit simplified, scenario:</span></span>

-   <span data-ttu-id="5eafa-130">Sven und Andrea geben einander einen geheimen Schlüssel weiter und einigen sich darauf, die MAC-Funktion zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="5eafa-130">Bob and Alice share a secret key and agree on a MAC function to use.</span></span>
-   <span data-ttu-id="5eafa-131">Sven schreibt eine Nachricht und gibt sie zusammen mit dem geheimen Schlüssel in eine MAC-Funktion ein, um einen MAC-Wert zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5eafa-131">Bob creates a message and inputs the message and the secret key into a MAC function to retrieve a MAC value.</span></span>
-   <span data-ttu-id="5eafa-132">Sven sendet die (nicht verschlüsselte) Nachricht und den MAC-Wert über ein Netzwerk an Andrea.</span><span class="sxs-lookup"><span data-stu-id="5eafa-132">Bob sends the \[unencrypted\] message and the MAC value to Alice over a network.</span></span>
-   <span data-ttu-id="5eafa-133">Andrea gibt den geheimen Schlüssel und die Nachricht ebenfalls in eine MAC-Funktion ein.</span><span class="sxs-lookup"><span data-stu-id="5eafa-133">Alice uses the secret key and the message as input to the MAC function.</span></span> <span data-ttu-id="5eafa-134">Sie vergleicht den MAC-Wert, den sie erhält, mit dem MAC-Wert, den Sie von Sven erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="5eafa-134">She compares the generated MAC value to the MAC value sent by Bob.</span></span> <span data-ttu-id="5eafa-135">Stimmen die Werte überein, wurde die Nachricht beim Verwenden nicht manipuliert.</span><span class="sxs-lookup"><span data-stu-id="5eafa-135">If they are the same, the message was not changed in transit.</span></span>

<span data-ttu-id="5eafa-136">Beachten Sie, dass Andrea eine unverschlüsselte Nachricht gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="5eafa-136">Note that Alice sent an unencrypted message.</span></span> <span data-ttu-id="5eafa-137">Nur der Hash war verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="5eafa-137">Only the hash was encrypted.</span></span> <span data-ttu-id="5eafa-138">Durch das Verfahren wird nur sichergestellt, dass die ursprüngliche Nachricht nicht verändert wurde und – durch die Verwendung von Andreas öffentlichem Schlüssel – dass der Nachrichtenhash von jemandem mit Zugriff auf Andreas privaten Schlüssel signiert wurde (wahrscheinlich von Andrea).</span><span class="sxs-lookup"><span data-stu-id="5eafa-138">The procedure ensures only that the original message was not altered and, by using Alice's public key, that the message hash was signed by someone with access to Alice's private key, presumably Alice.</span></span>

<span data-ttu-id="5eafa-139">Sie können die [**HashAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241511)-Klasse verwenden, um die verfügbaren Hashalgorithmen aufzulisten und einen [**CryptographicHash**](https://msdn.microsoft.com/library/windows/apps/br241498)-Wert zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5eafa-139">You can use the [**HashAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241511) class to enumerate the available hash algorithms and create a [**CryptographicHash**](https://msdn.microsoft.com/library/windows/apps/br241498) value.</span></span>

<span data-ttu-id="5eafa-140">Digitale Signaturen von öffentlichen Schlüsseln sind das Äquivalent der Nachrichtenauthentifizierungscodes (MACs) von privaten Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="5eafa-140">Digital signatures are the public key equivalent of private key message authentication codes (MACs).</span></span> <span data-ttu-id="5eafa-141">Während MACs private Schlüssel verwenden, um einem Nachrichtenempfänger das Überprüfen der Nachrichtenintegrität zu ermöglichen, verwenden Signaturen ein privates/öffentliches Schlüsselpaar.</span><span class="sxs-lookup"><span data-stu-id="5eafa-141">Whereas MACs use private keys to enable a message recipient to verify that a message has not been altered during transmission, signatures use a private/public key pair.</span></span>

<span data-ttu-id="5eafa-142">Mit dem [**CryptographicHash**](https://msdn.microsoft.com/library/windows/apps/br241498)-Objekt kann ein Hash mehrmals auf unterschiedliche Daten angewendet werden, ohne dass das Objekt jedes Mal neu erstellt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5eafa-142">The [**CryptographicHash**](https://msdn.microsoft.com/library/windows/apps/br241498) object can be used to repeatedly hash different data without having to re-create the object for each use.</span></span> <span data-ttu-id="5eafa-143">Die [**Append**](https://msdn.microsoft.com/library/windows/apps/br241499)-Methode fügt einem Puffer, auf den ein Hash angewendet werden soll, neue Daten hinzu.</span><span class="sxs-lookup"><span data-stu-id="5eafa-143">The [**Append**](https://msdn.microsoft.com/library/windows/apps/br241499) method adds new data to a buffer to be hashed.</span></span> <span data-ttu-id="5eafa-144">Die [**GetValueAndReset**](https://msdn.microsoft.com/library/windows/apps/hh701376)-Methode wendet den Hash auf die Daten an und setzt das Objekt zur weiteren Verwendung zurück.</span><span class="sxs-lookup"><span data-stu-id="5eafa-144">The [**GetValueAndReset**](https://msdn.microsoft.com/library/windows/apps/hh701376) method hashes the data and resets the object for another use.</span></span> <span data-ttu-id="5eafa-145">Dies wird im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="5eafa-145">This is shown by the following example.</span></span>

```cs
public void SampleReusableHash()
{
    // Create a string that contains the name of the hashing algorithm to use.
    String strAlgName = HashAlgorithmNames.Sha512;

    // Create a HashAlgorithmProvider object.
    HashAlgorithmProvider objAlgProv = HashAlgorithmProvider.OpenAlgorithm(strAlgName);

    // Create a CryptographicHash object. This object can be reused to continually
    // hash new messages.
    CryptographicHash objHash = objAlgProv.CreateHash();

    // Hash message 1.
    String strMsg1 = "This is message 1.";
    IBuffer buffMsg1 = CryptographicBuffer.ConvertStringToBinary(strMsg1, BinaryStringEncoding.Utf16BE);
    objHash.Append(buffMsg1);
    IBuffer buffHash1 = objHash.GetValueAndReset();

    // Hash message 2.
    String strMsg2 = "This is message 2.";
    IBuffer buffMsg2 = CryptographicBuffer.ConvertStringToBinary(strMsg2, BinaryStringEncoding.Utf16BE);
    objHash.Append(buffMsg2);
    IBuffer buffHash2 = objHash.GetValueAndReset();

    // Hash message 3.
    String strMsg3 = "This is message 3.";
    IBuffer buffMsg3 = CryptographicBuffer.ConvertStringToBinary(strMsg3, BinaryStringEncoding.Utf16BE);
    objHash.Append(buffMsg3);
    IBuffer buffHash3 = objHash.GetValueAndReset();

    // Convert the hashes to string values (for display);
    String strHash1 = CryptographicBuffer.EncodeToBase64String(buffHash1);
    String strHash2 = CryptographicBuffer.EncodeToBase64String(buffHash2);
    String strHash3 = CryptographicBuffer.EncodeToBase64String(buffHash3);
}

```

## <a name="digital-signatures"></a><span data-ttu-id="5eafa-146">Digitale Signaturen</span><span class="sxs-lookup"><span data-stu-id="5eafa-146">Digital signatures</span></span>


<span data-ttu-id="5eafa-147">Digitale Signaturen von öffentlichen Schlüsseln sind das Äquivalent der Nachrichtenauthentifizierungscodes (MACs) von privaten Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="5eafa-147">Digital signatures are the public key equivalent of private key message authentication codes (MACs).</span></span> <span data-ttu-id="5eafa-148">Während MACs private Schlüssel verwenden, um einem Nachrichtenempfänger das Überprüfen der Nachrichtenintegrität zu ermöglichen, verwenden Signaturen ein privates/öffentliches Schlüsselpaar.</span><span class="sxs-lookup"><span data-stu-id="5eafa-148">Whereas MACs use private keys to enable a message recipient to verify that a message has not been altered during transmission, signatures use a private/public key pair.</span></span>

<span data-ttu-id="5eafa-149">Da die meisten Signaturvorgänge für öffentliche Schlüssel rechtenintensiv sind, ist das Signieren eines Nachrichtenhashes in der Regel aber effizienter als das Signieren der ursprünglichen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="5eafa-149">Because most public key signature operations are computationally intensive, however, it is typically more efficient to sign (encrypt) a message hash than it is to sign the original message.</span></span> <span data-ttu-id="5eafa-150">Der Absender erstellt einen Nachrichtenhash, signiert ihn und sendet sowohl die Signatur als auch die (unverschlüsselte) Nachricht.</span><span class="sxs-lookup"><span data-stu-id="5eafa-150">The sender creates a message hash, signs it, and sends both the signature and the (unencrypted) message.</span></span> <span data-ttu-id="5eafa-151">Der Empfänger berechnet einen Hash für die Nachricht, entschlüsselt die Signatur und vergleicht die entschlüsselte Signatur mit dem Hashwert.</span><span class="sxs-lookup"><span data-stu-id="5eafa-151">The recipient calculates a hash over the message, decrypts the signature, and compares the decrypted signature to the hash value.</span></span> <span data-ttu-id="5eafa-152">Stimmen sie überein, kann der Empfänger relativ sicher sein, dass die Nachricht tatsächlich vom Absender stammt und während der Übertragung nicht manipuliert wurde.</span><span class="sxs-lookup"><span data-stu-id="5eafa-152">If they match, the recipient can be fairly certain that the message did, in fact, come from the sender and was not altered during transmission.</span></span>

<span data-ttu-id="5eafa-153">Durch das Signieren wird nur sichergestellt, dass die ursprüngliche Nachricht nicht verändert wurde und – durch die Verwendung des öffentlichen Schlüssels des Absenders – dass der Nachrichtenhash von jemandem mit Zugriff auf den privaten Schlüssel signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="5eafa-153">Signing ensures only that the original message was not altered and, by using the sender's public key, that the message hash was signed by someone with access to the private key.</span></span>

<span data-ttu-id="5eafa-154">Sie können ein [**AsymmetricKeyAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241478)-Objekt verwenden, um die verfügbaren Signaturalgorithmen aufzulisten und ein Schlüsselpaar zu generieren oder zu importieren.</span><span class="sxs-lookup"><span data-stu-id="5eafa-154">You can use an [**AsymmetricKeyAlgorithmProvider**](https://msdn.microsoft.com/library/windows/apps/br241478) object to enumerate the available signature algorithms and generate or import a key pair.</span></span> <span data-ttu-id="5eafa-155">Sie können statische Methoden der [**CryptographicHash**](https://msdn.microsoft.com/library/windows/apps/br241498)-Klasse zum Signieren einer Nachricht oder Überprüfen einer Signatur verwenden.</span><span class="sxs-lookup"><span data-stu-id="5eafa-155">You can use static methods on the [**CryptographicHash**](https://msdn.microsoft.com/library/windows/apps/br241498) class to sign a message or verify a signature.</span></span>