---
title: Schwerwiegender Fehler C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: 3b016790220d409435ff7ea53c6f48899a9e8f1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204346"
---
# <a name="fatal-error-c1067"></a>Schwerwiegender Fehler C1067

Compilerlimit: das Limit von 64K für die Größe eines Typdaten Satzes wurde überschritten.

Dieser Fehler kann auftreten, wenn ein Symbol einen ergänzten Namen hat, der mehr als 247 Zeichen enthält.  Um das Problem zu beheben, kürzen Sie den Symbolnamen.

Wenn der Compiler Debuginformationen generiert, gibt er Typdaten Sätze zum Definieren von Typen aus, die im Quellcode gefunden werden.  Beispielsweise enthalten die Typdaten Sätze einfache Strukturen und Argumentlisten von Funktionen.  Einige dieser Typen von Datensätzen können große Listen sein.

Die Größe eines beliebigen Typen Datensatzes beträgt 64 KB.  Wenn das Limit von 64K überschritten wird, tritt dieser Fehler auf.

C1067 kann auch auftreten, wenn viele Symbole mit langen Namen vorhanden sind oder wenn eine Klasse, Struktur oder Union zu viele Elemente aufweist.
