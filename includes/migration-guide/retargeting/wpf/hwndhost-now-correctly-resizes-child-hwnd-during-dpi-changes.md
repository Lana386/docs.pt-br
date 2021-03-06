---
ms.openlocfilehash: b92086c8ccf7592ce70b75bd31d4ea255c35b543
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803532"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>Agora o HwndHost redimensiona corretamente HWND filho durante alterações de DPI

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.2 e versões anteriores, quando o WPF estava sendo executado no modo Com reconhecimento por monitor, os controles hospedados em <xref:System.Windows.Interop.HwndHost> não foram dimensionados corretamente após alterações de DPI, por exemplo, ao migrar aplicativos de um monitor para outro. Com essa correção, os controles hospedados são dimensionados apropriadamente.|
|Sugestão|Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.7.2 ou posterior e aceitar esse comportamento definindo o seguinte comutador [AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) na seção <code>&lt;runtime&gt;</code> do arquivo de configuração do aplicativo <code>false</code>, conforme mostrado pelo exemplo a seguir.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Principal|
|Versão|4.8|
|Type|Redirecionando|
