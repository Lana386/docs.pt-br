---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803094"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Controles de host do navegador gerenciado do .NET Framework 1.1 e 2.0 estão bloqueados

|   |   |
|---|---|
|Detalhes|Hospedar esses controles é bloqueado no Internet Explorer.|
|Sugestão|O Internet Explorer falhará ao iniciar um aplicativo que usa o navegador gerenciado que hospeda controles. O comportamento anterior pode ser restaurado definindo o valor EnableIEHosting da subchave do registro <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> para <code>1</code> para sistemas x86 e para processos de 32 bits em sistemas de x64, e definindo o valor <code>EnableIEHosting</code> da subchave do registro <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> para <code>1</code> para processos de 64 bits em sistemas de x64.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
