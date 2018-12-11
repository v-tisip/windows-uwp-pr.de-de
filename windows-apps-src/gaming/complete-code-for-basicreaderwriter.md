---
title: Vollständiger Code für "BasicReaderWriter"
description: Vollständiger Code für eine Klasse und Methoden zum allgemeinen Lesen und Schreiben von Binärdatendateien.
ms.assetid: af968edd-df5c-b8e6-479e-bfa9689380fc
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, BasicReaderWriter
ms.localizationpriority: medium
ms.openlocfilehash: 60c2bf74de1e56004f1f705f317bc6bd1bb34b26
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8925108"
---
# <a name="complete-code-for-basicreaderwriter"></a><span data-ttu-id="8fb6e-104">Vollständiger Code für "BasicReaderWriter"</span><span class="sxs-lookup"><span data-stu-id="8fb6e-104">Complete code for BasicReaderWriter</span></span>



<span data-ttu-id="8fb6e-105">Vollständiger Code für eine Klasse und Methoden zum allgemeinen Lesen und Schreiben von Binärdatendateien.</span><span class="sxs-lookup"><span data-stu-id="8fb6e-105">Complete code for a class and methods for reading and writing binary data files in general.</span></span> <span data-ttu-id="8fb6e-106">Wird von der [BasicLoader](complete-code-for-basicloader.md)-Klasse verwendet.</span><span class="sxs-lookup"><span data-stu-id="8fb6e-106">Used by the [BasicLoader](complete-code-for-basicloader.md) class.</span></span>

<span data-ttu-id="8fb6e-107">Dieses Thema enthält die folgenden Abschnitte:</span><span class="sxs-lookup"><span data-stu-id="8fb6e-107">This topic contains these sections:</span></span>

-   [<span data-ttu-id="8fb6e-108">Technologien</span><span class="sxs-lookup"><span data-stu-id="8fb6e-108">Technologies</span></span>](#technologies)
-   [<span data-ttu-id="8fb6e-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8fb6e-109">Requirements</span></span>](#requirements)
-   [<span data-ttu-id="8fb6e-110">Anzeigen des Codes (C++)</span><span class="sxs-lookup"><span data-stu-id="8fb6e-110">View the code (C++)</span></span>](#view-the-code-c)


## <a name="download-location"></a><span data-ttu-id="8fb6e-111">Downloadort</span><span class="sxs-lookup"><span data-stu-id="8fb6e-111">Download location</span></span>

<span data-ttu-id="8fb6e-112">Dieses Beispiel kann nicht heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="8fb6e-112">This sample is not available for download.</span></span>


## <a name="technologies"></a><span data-ttu-id="8fb6e-113">Technologien</span><span class="sxs-lookup"><span data-stu-id="8fb6e-113">Technologies</span></span>

<span data-ttu-id="8fb6e-114">**Programmiersprachen** – C++</span><span class="sxs-lookup"><span data-stu-id="8fb6e-114">**Programming languages** -  C++</span></span>  
<span data-ttu-id="8fb6e-115">**Programmiermodelle** – Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="8fb6e-115">**Programming models** - Windows Runtime</span></span>


## <a name="requirements"></a><span data-ttu-id="8fb6e-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8fb6e-116">Requirements</span></span>

 <span data-ttu-id="8fb6e-117">**Unterstützte Mindestversion (Client)** – Windows 10</span><span class="sxs-lookup"><span data-stu-id="8fb6e-117">**Minimum supported client** - Windows 10</span></span>       
 <span data-ttu-id="8fb6e-118">**Unterstützte Mindestversion (Server)** – Windows Server 2016 Technical Preview</span><span class="sxs-lookup"><span data-stu-id="8fb6e-118">**Minimum supported server** - Windows Server 2016 Technical Preview</span></span> 

## <a name="view-the-code-c"></a><span data-ttu-id="8fb6e-119">Anzeigen des Codes (C++)</span><span class="sxs-lookup"><span data-stu-id="8fb6e-119">View the code (C++)</span></span>


## <a name="basicreaderwriterh"></a><span data-ttu-id="8fb6e-120">BasicReaderWriter.h</span><span class="sxs-lookup"><span data-stu-id="8fb6e-120">BasicReaderWriter.h</span></span>


```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

#include <ppltasks.h>

// A simple reader/writer class that provides support for reading and writing
// files on disk. Provides synchronous and asynchronous methods.
ref class BasicReaderWriter
{
private:
    Windows::Storage::StorageFolder^ m_location;
    Platform::String^ m_locationPath;

internal:
    BasicReaderWriter();
    BasicReaderWriter(
        _In_ Windows::Storage::StorageFolder^ folder
        );

    Platform::Array<byte>^ ReadData(
        _In_ Platform::String^ filename
        );

    concurrency::task<Platform::Array<byte>^> ReadDataAsync(
        _In_ Platform::String^ filename
        );

    uint32 WriteData(
        _In_ Platform::String^ filename,
        _In_ const Platform::Array<byte>^ fileData
        );

    concurrency::task<void> WriteDataAsync(
        _In_ Platform::String^ filename,
        _In_ const Platform::Array<byte>^ fileData
        );
};
```

## <a name="basicreaderwritercpp"></a><span data-ttu-id="8fb6e-121">BasicReaderWriter.cpp</span><span class="sxs-lookup"><span data-stu-id="8fb6e-121">BasicReaderWriter.cpp</span></span>


```cpp
using namespace Microsoft::WRL;
using namespace Windows::Storage;
using namespace Windows::Storage::FileProperties;
using namespace Windows::Storage::Streams;
using namespace Windows::Foundation;
using namespace Windows::ApplicationModel;
using namespace concurrency;

BasicReaderWriter::BasicReaderWriter()
{
    m_location = Package::Current->InstalledLocation;
    m_locationPath = Platform::String::Concat(m_location->Path, "\\");
}

BasicReaderWriter::BasicReaderWriter(
    _In_ Windows::Storage::StorageFolder^ folder
    )
{
    m_location = folder;
    Platform::String^ path = m_location->Path;
    if (path->Length() == 0)
    {
        // Applications are not permitted to access certain
        // folders, such as the Documents folder, using this
        // code path.  In such cases, the Path property for
        // the folder will be an empty string.
        throw ref new Platform::FailureException();
    }
    m_locationPath = Platform::String::Concat(path, "\\");
}

Platform::Array<byte>^ BasicReaderWriter::ReadData(
    _In_ Platform::String^ filename
    )
{
    CREATEFILE2_EXTENDED_PARAMETERS extendedParams = {0};
    extendedParams.dwSize = sizeof(CREATEFILE2_EXTENDED_PARAMETERS);
    extendedParams.dwFileAttributes = FILE_ATTRIBUTE_NORMAL;
    extendedParams.dwFileFlags = FILE_FLAG_SEQUENTIAL_SCAN;
    extendedParams.dwSecurityQosFlags = SECURITY_ANONYMOUS;
    extendedParams.lpSecurityAttributes = nullptr;
    extendedParams.hTemplateFile = nullptr;

    Wrappers::FileHandle file(
        CreateFile2(
            Platform::String::Concat(m_locationPath, filename)->Data(),
            GENERIC_READ,
            FILE_SHARE_READ,
            OPEN_EXISTING,
            &extendedParams
            )
        );
    if (file.Get() == INVALID_HANDLE_VALUE)
    {
        throw ref new Platform::FailureException();
    }

    FILE_STANDARD_INFO fileInfo = {0};
    if (!GetFileInformationByHandleEx(
        file.Get(),
        FileStandardInfo,
        &fileInfo,
        sizeof(fileInfo)
        ))
    {
        throw ref new Platform::FailureException();
    }

    if (fileInfo.EndOfFile.HighPart != 0)
    {
        throw ref new Platform::OutOfMemoryException();
    }

    Platform::Array<byte>^ fileData = ref new Platform::Array<byte>(fileInfo.EndOfFile.LowPart);

    if (!ReadFile(
        file.Get(),
        fileData->Data,
        fileData->Length,
        nullptr,
        nullptr
        ))
    {
        throw ref new Platform::FailureException();
    }

    return fileData;
}

task<Platform::Array<byte>^> BasicReaderWriter::ReadDataAsync(
    _In_ Platform::String^ filename
    )
{
    return task<StorageFile^>(m_location->GetFileAsync(filename)).then([=](StorageFile^ file)
    {
        return FileIO::ReadBufferAsync(file);
    }).then([=](IBuffer^ buffer)
    {
        auto fileData = ref new Platform::Array<byte>(buffer->Length);
        DataReader::FromBuffer(buffer)->ReadBytes(fileData);
        return fileData;
    });
}

uint32 BasicReaderWriter::WriteData(
    _In_ Platform::String^ filename,
    _In_ const Platform::Array<byte>^ fileData
    )
{
    CREATEFILE2_EXTENDED_PARAMETERS extendedParams = {0};
    extendedParams.dwSize = sizeof(CREATEFILE2_EXTENDED_PARAMETERS);
    extendedParams.dwFileAttributes = FILE_ATTRIBUTE_NORMAL;
    extendedParams.dwFileFlags = FILE_FLAG_SEQUENTIAL_SCAN;
    extendedParams.dwSecurityQosFlags = SECURITY_ANONYMOUS;
    extendedParams.lpSecurityAttributes = nullptr;
    extendedParams.hTemplateFile = nullptr;

    Wrappers::FileHandle file(
        CreateFile2(
            Platform::String::Concat(m_locationPath, filename)->Data(),
            GENERIC_WRITE,
            0,
            CREATE_ALWAYS,
            &extendedParams
            )
        );
    if (file.Get() == INVALID_HANDLE_VALUE)
    {
        throw ref new Platform::FailureException();
    }

    DWORD numBytesWritten;
    if (
        !WriteFile(
            file.Get(),
            fileData->Data,
            fileData->Length,
            &numBytesWritten,
            nullptr
            ) ||
        numBytesWritten != fileData->Length
        )
    {
        throw ref new Platform::FailureException();
    }

    return numBytesWritten;
}

task<void> BasicReaderWriter::WriteDataAsync(
    _In_ Platform::String^ filename,
    _In_ const Platform::Array<byte>^ fileData
    )
{
    return task<StorageFile^>(m_location->CreateFileAsync(filename, CreationCollisionOption::ReplaceExisting)).then([=](StorageFile^ file)
    {
        FileIO::WriteBytesAsync(file, fileData);
    });
}
```

 

 




