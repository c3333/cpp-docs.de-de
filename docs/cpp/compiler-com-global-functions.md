---
title: Globale COM-Funktionen des Compilers
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: c0a9c742ad9dcbb05ed2d78c954d5a597e3b57cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189779"
---
# <a name="compiler-com-global-functions"></a>Globale COM-Funktionen des Compilers

**Microsoft-spezifisch**

Die folgenden Routinen sind verfügbar:

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Löst eine [_com_error](../cpp/com-error-class.md) als Reaktion auf einen Fehler aus.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Ersetzt die Standardfunktion für die COM-Fehlerbehandlung.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Konvertiert einen `BSTR`-Wert in einen `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Konvertiert einen `char *`-Wert in einen `BSTR`.|

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Compilerklassen für COM-Unterstützung](../cpp/compiler-com-support-classes.md)<br/>
[COM-Unterstützung des Compilers](../cpp/compiler-com-support.md)
