---
title: Credenciais de chamada-gRPC para desenvolvedores do WCF
description: Como implementar e usar as credenciais de chamada do gRPC no ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 483f540a0ed3849883c07cc70f0e3d45a6b121ad
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184592"
---
# <a name="call-credentials"></a><span data-ttu-id="8886d-103">Chamar credenciais</span><span class="sxs-lookup"><span data-stu-id="8886d-103">Call credentials</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="8886d-104">As credenciais de chamada são todas baseadas em algum tipo de token passado em metadados com cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="8886d-104">Call credentials are all based on some kind of token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="8886d-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="8886d-105">WS-Federation</span></span>

<span data-ttu-id="8886d-106">O ASP.NET Core dá suporte ao WS-Federation usando o pacote NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="8886d-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="8886d-107">O WS-Federation é a alternativa disponível mais próxima à autenticação do Windows, que não tem suporte por HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="8886d-107">WS-Federation is the closest available alternative to Windows Authentication, which is not supported over HTTP/2.</span></span> <span data-ttu-id="8886d-108">Os usuários são autenticados usando o Serviços de Federação do Active Directory (AD FS) (ADFS), que fornece um token que pode ser usado para autenticar com ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8886d-108">Users are authenticated using Active Directory Federation Services (ADFS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="8886d-109">Para obter mais informações sobre como começar a usar esse método de autenticação, consulte o artigo [autenticar usuários com o WS-Federation no ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="8886d-109">For more information on how to get started with this authentication method, see the [Authenticate users with WS-Federation in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) article.</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="8886d-110">Tokens de portador JWT</span><span class="sxs-lookup"><span data-stu-id="8886d-110">JWT Bearer tokens</span></span>

<span data-ttu-id="8886d-111">O padrão de [token Web JSON](https://jwt.io) fornece uma maneira de codificar informações sobre um usuário e suas declarações em uma cadeia de caracteres codificada e assinar esse token de forma que o consumidor possa verificar a integridade do token usando criptografia de chave pública.</span><span class="sxs-lookup"><span data-stu-id="8886d-111">The [JSON Web Token](https://jwt.io) standard provides a way to encode information about a user and their claims in an encoded string, and to sign that token in such a way that the consumer can verify the integrity of the token using public key cryptography.</span></span> <span data-ttu-id="8886d-112">Você pode usar vários serviços, como IdentityServer4, para autenticar usuários e gerar tokens de OpenID Connect (OIDC) para usar com APIs de gRPC e HTTP.</span><span class="sxs-lookup"><span data-stu-id="8886d-112">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="8886d-113">ASP.NET Core 3,0 pode manipular tokens Web JSON usando o pacote de portador JWT.</span><span class="sxs-lookup"><span data-stu-id="8886d-113">ASP.NET Core 3.0 can handle JSON Web Tokens using the JWT Bearer package.</span></span> <span data-ttu-id="8886d-114">A configuração é exatamente a mesma para um aplicativo gRPC como um aplicativo MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8886d-114">The configuration is exactly the same for a gRPC application as an ASP.NET Core MVC application.</span></span>

<span data-ttu-id="8886d-115">Este capítulo se concentrará em tokens de portador JWT, pois eles são mais fáceis de desenvolver com o WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="8886d-115">This chapter will focus on JWT Bearer tokens as they're easier to develop with than WS-Federation.</span></span>

## <a name="adding-authentication-and-authorization-to-the-server"></a><span data-ttu-id="8886d-116">Adicionando autenticação e autorização ao servidor</span><span class="sxs-lookup"><span data-stu-id="8886d-116">Adding authentication and authorization to the server</span></span>

<span data-ttu-id="8886d-117">O pacote de portador JWT não está incluído no ASP.NET Core 3,0 por padrão.</span><span class="sxs-lookup"><span data-stu-id="8886d-117">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="8886d-118">Instale o pacote NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8886d-118">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="8886d-119">Adicione o serviço de autenticação na classe de inicialização e configure o manipulador de portador JWT.</span><span class="sxs-lookup"><span data-stu-id="8886d-119">Add the Authentication service in the Startup class and configure the JWT Bearer handler.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="8886d-120">A `IssuerSigningKey` propriedade requer uma implementação de `Microsoft.IdentityModels.Tokens.SecurityKey` com os dados criptográficos necessários para validar os tokens assinados.</span><span class="sxs-lookup"><span data-stu-id="8886d-120">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="8886d-121">Esse token deve ser armazenado com segurança em um *servidor de segredos* , como o Azure keyvault.</span><span class="sxs-lookup"><span data-stu-id="8886d-121">This token should be stored securely in a *secrets server* like Azure KeyVault.</span></span>

<span data-ttu-id="8886d-122">Em seguida, adicione o serviço de autorização, que controla o acesso ao sistema.</span><span class="sxs-lookup"><span data-stu-id="8886d-122">Next add the Authorization service, which controls access to the system.</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="8886d-123">Autenticação e autorização são duas etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="8886d-123">Authentication and Authorization are two separate steps.</span></span> <span data-ttu-id="8886d-124">A autenticação é usada para determinar a identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="8886d-124">Authentication is used to determine the user's identity.</span></span> <span data-ttu-id="8886d-125">A autorização decide se esse usuário tem permissão para acessar várias partes do sistema.</span><span class="sxs-lookup"><span data-stu-id="8886d-125">Authorization decides whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="8886d-126">Agora, adicione o middleware de autenticação e autorização ao pipeline ASP.NET Core no `Configure` método.</span><span class="sxs-lookup"><span data-stu-id="8886d-126">Now add the Authentication and Authorization middleware to the ASP.NET Core pipeline in the `Configure` method.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="8886d-127">Por fim, aplique `[Authorize]` o atributo a qualquer serviço ou método a ser protegido e use a `User` Propriedade do subjacente `HttpContext` para verificar as permissões.</span><span class="sxs-lookup"><span data-stu-id="8886d-127">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="providing-call-credentials-in-the-client-application"></a><span data-ttu-id="8886d-128">Fornecendo credenciais de chamada no aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="8886d-128">Providing call credentials in the client application</span></span>

<span data-ttu-id="8886d-129">Depois de obter um token JWT de um servidor de identidade, você pode usá-lo para autenticar chamadas gRPC do cliente adicionando-o como um cabeçalho de metadados na chamada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8886d-129">Once you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="8886d-130">Agora, você protegeu o serviço gRPC usando tokens de portador JWT como credenciais de chamada.</span><span class="sxs-lookup"><span data-stu-id="8886d-130">Now, you've secured your gRPC service using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="8886d-131">Uma versão do [aplicativo gRPC de exemplo de portfólios com autenticação e autorização adicionada](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) está no github.</span><span class="sxs-lookup"><span data-stu-id="8886d-131">A version of the [Portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8886d-132">[Anterior](security.md)
>[Próximo](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="8886d-132">[Previous](security.md)
[Next](channel-credentials.md)</span></span>