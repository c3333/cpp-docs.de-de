---
title: Dateiberechtigungskonstanten
ms.date: 11/04/2016
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 9f6126b867e29ca37468c6ff383224a483639c78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443274"
---
# <a name="file-permission-constants"></a>Dateiberechtigungskonstanten

## <a name="syntax"></a>Syntax

```
#include <sys/stat.h>
```

## <a name="remarks"></a>Bemerkungen

Eine der folgenden Konstanten ist erforderlich, wenn `_O_CREAT` (`_open`, `_sopen`) angegeben wird.

Das `pmode`-Argument gibt die Dateiberechtigungseinstellungen wie folgt an.

|Dauerhaft|Bedeutung|
|--------------|-------------|
|`_S_IREAD`|Lesen erlaubt|
|`_S_IWRITE`|Schreiben erlaubt|
|`_S_IREAD` &#124; `_S_IWRITE`|Lesen und Schreiben erlaubt|

Bei Verwendung als `pmode`-Argument für `_umask` legt die Manifestkonstante die Berechtigungseinstellung wie folgt fest.

|Dauerhaft|Bedeutung|
|--------------|-------------|
|`_S_IREAD`|Schreiben nicht erlaubt (Datei ist schreibgeschützt)|
|`_S_IWRITE`|Lesen nicht erlaubt (Datei ist lesegeschützt)|
|`_S_IREAD` &#124; `_S_IWRITE`|Weder Lesen noch Schreiben erlaubt|

## <a name="see-also"></a>Weitere Informationen

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Standardtypen](../c-runtime-library/standard-types.md)<br/>
[Global Constants (Globale Konstanten)](../c-runtime-library/global-constants.md)
