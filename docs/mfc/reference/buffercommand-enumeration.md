---
title: Buffercommand-Enumeration
description: 'Beschreibt die buffercommand-Aufzählung, die für die Arbeit mit Speicherdateien über CMemFile:: getbufferptr () verwendet wird.'
ms.date: 07/23/2020
f1_keywords:
- afx/buffercommand
helpviewer_keywords:
- buffercommand enumeration [MFC]
ms.openlocfilehash: f2f553df56fadd99b65b04cce9a97917425ed70b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212070"
---
# <a name="buffercommand-enumeration"></a>Buffercommand-Enumeration

Wird von [CMemFile:: getbufferptr](cmemfile-class.md#getbufferptr) verwendet, um zu bestimmen, welche Aktion für den Datei gestützten Speicherpuffer ausgeführt werden soll.

## <a name="syntax"></a>Syntax

``` cpp
public enum BufferCommand
{
   bufferRead,
   bufferWrite,
   bufferCommit,
   bufferCheck
};
```

## <a name="members"></a>Member

|Name|BESCHREIBUNG|
|-|-|
| `bufferRead` | Lesen Sie den Datei gestützten Speicherpuffer. |
| `bufferWrite` | Schreiben in den Datei gestützten Speicherpuffer. |
| `bufferCommit` | Verschiebt die aktuelle Position im Datei gestützten Speicherpuffer auf das Ende des zugesicherten Puffers. |
| `bufferCheck` | Bestimmen Sie, ob die Größe des Datei gestützten Speicherpuffers vergrößert werden kann. |

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwinforms. h (in Assemblyatlmfc\lib\mfcmifc80.dll definiert)
