---
author: mtoepke
title: Portieren von OpenGLES2.0 zu Direct3D11
description: "Enthält Artikel, Übersichten und exemplarische Vorgehensweisen zum Portieren einer OpenGL ES 2.0-Grafikpipeline zu Direct3D 11 und zur Windows-Runtime."
ms.assetid: 1e1cf668-a15f-0c7b-8daf-3260d27c6d9c
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Opengl, Direct3D 11, Portieren, Grafiken
ms.openlocfilehash: 14ed2be84f295570dc95b3f1d28dfdd3720bada4
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="port-from-opengl-es-20-to-direct3d-11"></a>Portieren von OpenGL ES 2.0 zu Direct3D 11


\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Enthält Artikel, Übersichten und exemplarische Vorgehensweisen zum Portieren einer OpenGL ES 2.0-Grafikpipeline zu Direct3D 11 und zur Windows-Runtime.

> **Hinweis**   Ein Zwischenschritt zum Portieren Ihres OpenGL ES 2.0-Projekts ist die Verwendung von ANGLE für Windows Store. Mit ANGLE können Sie OpenGL ES-Inhalte unter Windows ausführen, indem Sie OpenGL ES-API-Aufrufe in DirectX11-API-Aufrufe übersetzen. Weitere Informationen zu ANGLE finden Sie im [ANGLE für Windows Store-Wiki](http://go.microsoft.com/fwlink/p/?linkid=618387).

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[Zuordnen von OpenGL ES 2.0 zu Direct3D 11,1](map-concepts-and-infrastructure.md)</p></td>
<td align="left"><p>Machen Sie sich zu Beginn des Prozesses zur ersten Portierung Ihrer Grafikarchitektur von OpenGL ES 2.0 zu Direct3D mit den Hauptunterschieden zwischen den APIs vertraut. Mithilfe der Themen in diesem Abschnitt können Sie die Portierungsstrategie und die API-Änderungen planen, die erforderlich sind, wenn Sie die Grafikverarbeitung auf Direct3D umstellen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[So wird's gemacht: Portieren eines einfachen OpenGLES2.0-Renderers zu Direct3D11.1](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md)</p></td>
<td align="left"><p>In dieser Portierungsübung beginnen wir mit den Grundlagen: Umstellen eines einfachen Renderers für einen sich drehenden Würfel mit Vertexschattierungen von OpenGLES2.0 auf Direct3D, damit er der Vorlage „DirectX11-App (Universelle Windows-App)“ aus Visual Studio2015 entspricht.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[OpenGLES2.0 zu Direct3D11.1 – Referenz](opengl-es-2-0-to-directx-11-1-reference.md)</p></td>
<td align="left"><p>Verwenden Sie diese Referenzthemen zum Suchen nach der API-Zuordnung und kurzen Codebeispielen, wenn Sie die Portierung von OpenGLES2.0 zu Direct3D11 durchführen.</p></td>
</tr>
</tbody>
</table>

 

> **Hinweis**  
Dieser Artikel ist für Windows10-Entwickler bestimmt, die Apps für die universelle Windows-Plattform (UWP) schreiben. Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).

 

 

 




