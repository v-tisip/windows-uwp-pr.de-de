---
title: Datenschutz
description: In diesem Artikel wird erläutert, wie Sie mithilfe der DataProtectionProvider-Klasse im Windows.Security.Cryptography.DataProtection-Namespace digitale Daten in einer UWP-App verschlüsseln und entschlüsseln können.
ms.assetid: 9EE3CC45-5C44-4196-BD8B-1D64EFC5C509
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: edcce656f5be681a11e79b4714e96c2dcde621d5
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6850123"
---
# <a name="data-protection"></a><span data-ttu-id="f5da3-104">Datenschutz</span><span class="sxs-lookup"><span data-stu-id="f5da3-104">Data protection</span></span>



<span data-ttu-id="f5da3-105">In diesem Artikel wird erläutert, wie Sie mithilfe der [**DataProtectionProvider**](https://msdn.microsoft.com/library/windows/apps/br241559)-Klasse im [**Windows.Security.Cryptography.DataProtection**](https://msdn.microsoft.com/library/windows/apps/br241585)-Namespace digitale Daten in einer UWP-App verschlüsseln und entschlüsseln können.</span><span class="sxs-lookup"><span data-stu-id="f5da3-105">This article explains how to use the [**DataProtectionProvider**](https://msdn.microsoft.com/library/windows/apps/br241559) class in the [**Windows.Security.Cryptography.DataProtection**](https://msdn.microsoft.com/library/windows/apps/br241585) namespace to encrypt and decrypt digital data in a UWP app.</span></span>

<span data-ttu-id="f5da3-106">Sie können die Datenschutz-APIs auf verschiedene Weise verwenden:</span><span class="sxs-lookup"><span data-stu-id="f5da3-106">You can use the data protection APIs in multiple ways:</span></span>

-   <span data-ttu-id="f5da3-107">Zum Schützen von Daten durch einen Active Directory-Sicherheitsprinzipal (AD), wie z. B. eine AD-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="f5da3-107">To protect data to an Active Directory (AD) security principal like an AD group.</span></span> <span data-ttu-id="f5da3-108">Jedes Mitglied der Gruppe kann die Daten entschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="f5da3-108">Any member of the group can decrypt the data.</span></span>
-   <span data-ttu-id="f5da3-109">Zum Schützen von Daten durch einen öffentlichen Schlüssel, der in einem X.509-Zertifikat enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="f5da3-109">To protect data to the public key contained in an X.509 certificate.</span></span> <span data-ttu-id="f5da3-110">Der Besitzer eines privaten Schlüssels kann die Daten entschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="f5da3-110">The owner of the private key can decrypt the data.</span></span>
-   <span data-ttu-id="f5da3-111">Zum Schützen von Daten mithilfe eines symmetrischen Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="f5da3-111">To protect data by using a symmetric key.</span></span> <span data-ttu-id="f5da3-112">Damit können zum Beispiel die Daten eines Nicht-AD-Prinzipals wie Live ID geschützt werden.</span><span class="sxs-lookup"><span data-stu-id="f5da3-112">This works, for example, to protect data to a non-AD principal such as Live ID.</span></span>
-   <span data-ttu-id="f5da3-113">Zum Schützen von Daten anhand von Anmeldeinformationen (Kennwort), die zum Anmelden bei einer Website erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f5da3-113">To protect data to the credentials (password) used during logon to a website.</span></span>

<span data-ttu-id="f5da3-114">Um Daten zu schützen, müssen Sie beim Erstellen eines [**DataProtectionProvider**](https://msdn.microsoft.com/library/windows/apps/br241559)-Objekts einen Schutzdeskriptor angeben, bevor Sie [**ProtectAsync**](https://msdn.microsoft.com/library/windows/apps/br241563) oder [**ProtectStreamAsync**](https://msdn.microsoft.com/library/windows/apps/br241564) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f5da3-114">To protect data, when you create a [**DataProtectionProvider**](https://msdn.microsoft.com/library/windows/apps/br241559) object you must specify a protection descriptor before calling [**ProtectAsync**](https://msdn.microsoft.com/library/windows/apps/br241563) or [**ProtectStreamAsync**](https://msdn.microsoft.com/library/windows/apps/br241564).</span></span> <span data-ttu-id="f5da3-115">Im Folgenden sehen Sie Beispiele für mögliche Schutzdeskriptoren.</span><span class="sxs-lookup"><span data-stu-id="f5da3-115">The following example shows possible sample protection descriptors.</span></span>

## <a name="protecting-static-data"></a><span data-ttu-id="f5da3-116">Schützen statischer Daten</span><span class="sxs-lookup"><span data-stu-id="f5da3-116">Protecting static data</span></span>


<span data-ttu-id="f5da3-117">Das folgende Beispiel zeigt, wie Sie mithilfe der Methoden [**ProtectAsync**](https://msdn.microsoft.com/library/windows/apps/br241563) und [**UnprotectAsync**](https://msdn.microsoft.com/library/windows/apps/br241565) statische Daten für die SID des aktuellen Benutzers asynchron schützen können.</span><span class="sxs-lookup"><span data-stu-id="f5da3-117">The following example shows how to use the [**ProtectAsync**](https://msdn.microsoft.com/library/windows/apps/br241563) and [**UnprotectAsync**](https://msdn.microsoft.com/library/windows/apps/br241565) methods to asynchronously protect static data to the current user's SID.</span></span>

```cs
using Windows.Security.Cryptography;
using Windows.Security.Cryptography.DataProtection;
using Windows.Storage.Streams;
using System.Threading.Tasks;

namespace SampleProtectAsync
{
    sealed partial class StaticDataProtectionApp : Application
    {
        public StaticDataProtectionApp()
        {
            // Initialize the application.
            this.InitializeComponent();

            // Protect data asynchronously.
            this.Protect();
        }

        public async void Protect()
        {
            // Initialize function arguments.
            String strMsg = "This is a message to be protected.";
            String strDescriptor = "LOCAL=user";
            BinaryStringEncoding encoding = BinaryStringEncoding.Utf8;

            // Protect a message to the local user.
            IBuffer buffProtected = await this.SampleProtectAsync(
                strMsg,
                strDescriptor,
                encoding);

            // Decrypt the previously protected message.
            String strDecrypted = await this.SampleUnprotectData(
                buffProtected,
                encoding);
        }

        public async Task<IBuffer> SampleProtectAsync(
            String strMsg,
            String strDescriptor,
            BinaryStringEncoding encoding)
        {
            // Create a DataProtectionProvider object for the specified descriptor.
            DataProtectionProvider Provider = new DataProtectionProvider(strDescriptor);

            // Encode the plaintext input message to a buffer.
            encoding = BinaryStringEncoding.Utf8;
            IBuffer buffMsg = CryptographicBuffer.ConvertStringToBinary(strMsg, encoding);

            // Encrypt the message.
            IBuffer buffProtected = await Provider.ProtectAsync(buffMsg);

            // Execution of the SampleProtectAsync function resumes here
            // after the awaited task (Provider.ProtectAsync) completes.
            return buffProtected;
        }

        public async Task<String> SampleUnprotectData(
            IBuffer buffProtected,
            BinaryStringEncoding encoding)
        {
            // Create a DataProtectionProvider object.
            DataProtectionProvider Provider = new DataProtectionProvider();

            // Decrypt the protected message specified on input.
            IBuffer buffUnprotected = await Provider.UnprotectAsync(buffProtected);

            // Execution of the SampleUnprotectData method resumes here
            // after the awaited task (Provider.UnprotectAsync) completes
            // Convert the unprotected message from an IBuffer object to a string.
            String strClearText = CryptographicBuffer.ConvertBinaryToString(encoding, buffUnprotected);

            // Return the plaintext string.
            return strClearText;
        }
    }
}
```

## <a name="protecting-stream-data"></a><span data-ttu-id="f5da3-118">Schützen von Datenstromdaten</span><span class="sxs-lookup"><span data-stu-id="f5da3-118">Protecting stream data</span></span>


<span data-ttu-id="f5da3-119">Das folgende Beispiel zeigt, wie Sie mithilfe der Methoden [**ProtectStreamAsync**](https://msdn.microsoft.com/library/windows/apps/br241564) und [**UnprotectStreamAsync**](https://msdn.microsoft.com/library/windows/apps/br241566) Datenstromdaten für die SID des aktuellen Benutzers asynchron schützen können.</span><span class="sxs-lookup"><span data-stu-id="f5da3-119">The following example shows how to use the [**ProtectStreamAsync**](https://msdn.microsoft.com/library/windows/apps/br241564) and [**UnprotectStreamAsync**](https://msdn.microsoft.com/library/windows/apps/br241566) methods to asynchronously protect stream data to the current user's SID.</span></span>

```cs
using Windows.Security.Cryptography;
using Windows.Security.Cryptography.DataProtection;
using Windows.Storage.Streams;
using System.Threading.Tasks;

namespace SampleProtectStreamAsync
{

    sealed partial class StreamDataProtectionApp : Application
    {
        public StreamDataProtectionApp()
        {
            // Initialize the application.
            this.InitializeComponent();

            // Protect a stream synchronously
            this.ProtectData();
         }

        public async void ProtectData()
        {
            // Initialize function arguments.
            String strDescriptor = "LOCAL=user";
            String strLoremIpsum = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse elementum "
                + "ullamcorper eros, vitae gravida nunc consequat sollicitudin. Vivamus lacinia, "
                + "diam a molestie porttitor, sapien neque volutpat est, non suscipit leo dolor "
                + "sit amet nisl. Praesent tincidunt tincidunt quam ut pharetra. Sed tincidunt "
                + "sit amet nisl. Praesent tincidunt tincidunt quam ut pharetra. Sed tincidunt "
                + "porttitor massa, at convallis dolor dictum suscipit. Nullam vitae lectus in "
                + "lorem scelerisque convallis sed scelerisque orci. Praesent sed ligula vel erat "
                + "eleifend tempus. Nullam dignissim aliquet mauris a aliquet. Nulla augue justo, "
                + "posuere a consectetur ut, suscipit et sem. Proin eu libero ut felis tincidunt "
                + "interdum. Curabitur vulputate eros nec sapien elementum ut dapibus eros "
                + "dapibus. Suspendisse quis dui dolor, non imperdiet leo. In consequat, odio nec "
                + "aliquam tincidunt, magna enim ultrices massa, ac pharetra est urna at arcu. "
                + "Nunc suscipit, velit non interdum suscipit, lectus lectus auctor tortor, quis "
                + "ultrices orci felis in dolor. Etiam congue pretium libero eu vestibulum. "
                + "Mauris bibendum erat eleifend nibh consequat eu pharetra metus convallis. "
                + "Morbi sem eros, venenatis vel vestibulum consequat, hendrerit rhoncus purus.";
            BinaryStringEncoding encoding = BinaryStringEncoding.Utf16BE;

            // Encrypt the data as a stream.
            IBuffer buffProtected = await this.SampleDataProtectionStream(
                strDescriptor,
                strLoremIpsum,
                encoding);

            // Decrypt a data stream.
            String strUnprotected = await this.SampleDataUnprotectStream(
                buffProtected,
                encoding);
        }

        public async Task<IBuffer> SampleDataProtectionStream(
            String descriptor,
            String strMsg,
            BinaryStringEncoding encoding)
        {
            // Create a DataProtectionProvider object for the specified descriptor.
            DataProtectionProvider Provider = new DataProtectionProvider(descriptor);

            // Convert the input string to a buffer.
            IBuffer buffMsg = CryptographicBuffer.ConvertStringToBinary(strMsg, encoding);

            // Create a random access stream to contain the plaintext message.
            InMemoryRandomAccessStream inputData = new InMemoryRandomAccessStream();

            // Create a random access stream to contain the encrypted message.
            InMemoryRandomAccessStream protectedData = new InMemoryRandomAccessStream();

            // Retrieve an IOutputStream object and fill it with the input (plaintext) data.
            IOutputStream outputStream = inputData.GetOutputStreamAt(0);
            DataWriter writer = new DataWriter(outputStream);
            writer.WriteBuffer(buffMsg);
            await writer.StoreAsync();
            await outputStream.FlushAsync();

            // Retrieve an IInputStream object from which you can read the input data.
            IInputStream source = inputData.GetInputStreamAt(0);

            // Retrieve an IOutputStream object and fill it with encrypted data.
            IOutputStream dest = protectedData.GetOutputStreamAt(0);
            await Provider.ProtectStreamAsync(source, dest);
            await dest.FlushAsync();

            //Verify that the protected data does not match the original
            DataReader reader1 = new DataReader(inputData.GetInputStreamAt(0));
            DataReader reader2 = new DataReader(protectedData.GetInputStreamAt(0));
            await reader1.LoadAsync((uint)inputData.Size);
            await reader2.LoadAsync((uint)protectedData.Size);
            IBuffer buffOriginalData = reader1.ReadBuffer((uint)inputData.Size);
            IBuffer buffProtectedData = reader2.ReadBuffer((uint)protectedData.Size);

            if (CryptographicBuffer.Compare(buffOriginalData, buffProtectedData))
            {
                throw new Exception("ProtectStreamAsync returned unprotected data");
            }

            // Return the encrypted data.
            return buffProtectedData;
        }

        public async Task<String> SampleDataUnprotectStream(
            IBuffer buffProtected,
            BinaryStringEncoding encoding)
        {
            // Create a DataProtectionProvider object.
            DataProtectionProvider Provider = new DataProtectionProvider();

            // Create a random access stream to contain the encrypted message.
            InMemoryRandomAccessStream inputData = new InMemoryRandomAccessStream();

            // Create a random access stream to contain the decrypted data.
            InMemoryRandomAccessStream unprotectedData = new InMemoryRandomAccessStream();

            // Retrieve an IOutputStream object and fill it with the input (encrypted) data.
            IOutputStream outputStream = inputData.GetOutputStreamAt(0);
            DataWriter writer = new DataWriter(outputStream);
            writer.WriteBuffer(buffProtected);
            await writer.StoreAsync();
            await outputStream.FlushAsync();

            // Retrieve an IInputStream object from which you can read the input (encrypted) data.
            IInputStream source = inputData.GetInputStreamAt(0);

            // Retrieve an IOutputStream object and fill it with decrypted data.
            IOutputStream dest = unprotectedData.GetOutputStreamAt(0);
            await Provider.UnprotectStreamAsync(source, dest);
            await dest.FlushAsync();

            // Write the decrypted data to an IBuffer object.
            DataReader reader2 = new DataReader(unprotectedData.GetInputStreamAt(0));
            await reader2.LoadAsync((uint)unprotectedData.Size);
            IBuffer buffUnprotectedData = reader2.ReadBuffer((uint)unprotectedData.Size);

            // Convert the IBuffer object to a string using the same encoding that was
            // used previously to conver the plaintext string (before encryption) to an
            // IBuffer object.
            String strUnprotected = CryptographicBuffer.ConvertBinaryToString(encoding, buffUnprotectedData);

            // Return the decrypted data.
            return strUnprotected;
        }
    }
}
```