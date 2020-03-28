---
title: dotnet nuget adicionar comando fonte
description: O comando dotnet nuget add source adiciona uma nova fonte de pacote aos seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148564"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="af89e-103">dotnet nuget adicionar fonte</span><span class="sxs-lookup"><span data-stu-id="af89e-103">dotnet nuget add source</span></span>

<span data-ttu-id="af89e-104">**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="af89e-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="af89e-105">Nome</span><span class="sxs-lookup"><span data-stu-id="af89e-105">Name</span></span>

<span data-ttu-id="af89e-106">`dotnet nuget add source`- Adicione uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="af89e-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="af89e-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="af89e-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="af89e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="af89e-108">Description</span></span>

<span data-ttu-id="af89e-109">O `dotnet nuget add source` comando adiciona uma nova fonte de pacote aos arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="af89e-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="af89e-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="af89e-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="af89e-111">Caminho para a fonte do pacote.</span><span class="sxs-lookup"><span data-stu-id="af89e-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="af89e-112">Opções</span><span class="sxs-lookup"><span data-stu-id="af89e-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="af89e-113">O arquivo de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="af89e-113">The NuGet configuration file.</span></span> <span data-ttu-id="af89e-114">Se especificado, apenas as configurações deste arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="af89e-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="af89e-115">Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="af89e-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="af89e-116">Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="af89e-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name`**

  <span data-ttu-id="af89e-117">Nome da fonte.</span><span class="sxs-lookup"><span data-stu-id="af89e-117">Name of the source.</span></span>

- **`-p|--password`**

  <span data-ttu-id="af89e-118">Senha a ser usada ao se conectar a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="af89e-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="af89e-119">Permite armazenar credenciais de origem de pacote portátil desabilitando a criptografia de senha.</span><span class="sxs-lookup"><span data-stu-id="af89e-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="af89e-120">Nome de usuário a ser usado ao se conectar a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="af89e-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="af89e-121">Lista separada por comma de tipos de autenticação válidos para esta fonte.</span><span class="sxs-lookup"><span data-stu-id="af89e-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="af89e-122">Defina `basic` isso para se o servidor anunciar NTLM ou Negociar e suas credenciais devem ser enviadas usando o mecanismo Básico, por exemplo, ao usar um PAT com o Azure DevOps Server no local.</span><span class="sxs-lookup"><span data-stu-id="af89e-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="af89e-123">Outros valores `negotiate` `kerberos`válidos incluem, `ntlm`e `digest`, mas esses valores são improváveis de serem úteis.</span><span class="sxs-lookup"><span data-stu-id="af89e-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="af89e-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="af89e-124">Examples</span></span>

- <span data-ttu-id="af89e-125">Adicionar `nuget.org` como fonte:</span><span class="sxs-lookup"><span data-stu-id="af89e-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="af89e-126">Adicionar `c:\packages` como fonte local:</span><span class="sxs-lookup"><span data-stu-id="af89e-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="af89e-127">Adicione uma fonte que precisa de autenticação:</span><span class="sxs-lookup"><span data-stu-id="af89e-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="af89e-128">Adicione uma fonte que precise de autenticação (em seguida, vá instalar provedor de credencial):</span><span class="sxs-lookup"><span data-stu-id="af89e-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="af89e-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="af89e-129">See also</span></span>

- [<span data-ttu-id="af89e-130">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="af89e-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="af89e-131">comando fontes (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="af89e-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)