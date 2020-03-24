---
title: Compilerfehler C3173
ms.date: 11/04/2016
f1_keywords:
- C3173
helpviewer_keywords:
- C3173
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
ms.openlocfilehash: 98b9b1b74bb8b4484026873f5c6052b5624c4f69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176467"
---
# <a name="compiler-error-c3173"></a>Compilerfehler C3173

Versions Konflikt beim IDL-Merge.

Dieser Fehler tritt auf, wenn eine Objektdatei eingebettete IDL enthält, die mit einer früheren Version des Compilers generiert wurde. Der Compiler codiert eine Versionsnummer, um sicherzustellen, dass derselbe Compiler, der zum Generieren der in die OBJ-Dateien eingebetteten IDL-Inhalte verwendet wird, auch derselbe Compiler ist, der zum Zusammenführen der eingebetteten IDL verwendet wird.

Aktualisieren Sie die C++ visuelle Installation, sodass alle Tools von der neuesten Version stammen.
