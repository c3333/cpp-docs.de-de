---
title: ATL_URL_SCHEME-Enumeration
ms.date: 11/04/2016
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
ms.openlocfilehash: 6d8307d6ea51c5ec7e63735360b8628a4c1ed782
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168578"
---
# <a name="atl_url_scheme"></a>ATL_URL_SCHEME

Die Member dieser Enumeration stellen Konstanten für die Schemas bereit, die von [CUrl](curl-class.md)verstanden werden.

## <a name="syntax"></a>Syntax

```cpp
enum ATL_URL_SCHEME{
   ATL_URL_SCHEME_UNKNOWN = -1,
   ATL_URL_SCHEME_FTP     = 0,
   ATL_URL_SCHEME_GOPHER  = 1,
   ATL_URL_SCHEME_HTTP    = 2,
   ATL_URL_SCHEME_HTTPS   = 3,
   ATL_URL_SCHEME_FILE    = 4,
   ATL_URL_SCHEME_NEWS    = 5,
   ATL_URL_SCHEME_MAILTO  = 6,
   ATL_URL_SCHEME_SOCKS   = 7
};
```

## <a name="requirements"></a>Anforderungen

**Header:** atlutil. h

## <a name="see-also"></a>Weitere Informationen:

[Konzepte](../active-template-library-atl-concepts.md)<br/>
[CUrl:: ab.](curl-class.md#setscheme)<br/>
[CUrl:: getscheme](curl-class.md#getscheme)
