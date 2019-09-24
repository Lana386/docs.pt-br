---
title: Enumerações Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como declarar e usar enumerações no Protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184235"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="a804c-103">Enumerações Protobuf</span><span class="sxs-lookup"><span data-stu-id="a804c-103">Protobuf enumerations</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a804c-104">O Protobuf dá suporte a tipos de enumeração, como visto na seção anterior, em que uma enumeração foi usada para `oneof` determinar o tipo de um campo.</span><span class="sxs-lookup"><span data-stu-id="a804c-104">Protobuf supports enumeration types, as seen in the previous section where an enum was used to determine the type of a `oneof` field.</span></span> <span data-ttu-id="a804c-105">Você pode definir seus próprios tipos de enumeração e Protobuf irá compilá- C# los para tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="a804c-105">You can define your own enumeration types and Protobuf will compile them to C# enum types.</span></span> <span data-ttu-id="a804c-106">Como Protobuf pode ser usado com idiomas diferentes, as convenções de nomenclatura para enumerações são diferentes das C# convenções.</span><span class="sxs-lookup"><span data-stu-id="a804c-106">Since Protobuf can be used with different languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="a804c-107">No entanto, o gerador de código é inteligente e converte os nomes C# para o caso tradicional.</span><span class="sxs-lookup"><span data-stu-id="a804c-107">However, the code generator is clever and converts the names to the traditional C# case.</span></span> <span data-ttu-id="a804c-108">Se o equivalente ao caso do Pascal do nome do campo começar com o nome da enumeração, ele será removido.</span><span class="sxs-lookup"><span data-stu-id="a804c-108">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="a804c-109">Por exemplo, nesta Enumeração Protobuf, os campos são prefixados `ACCOUNT_STATUS`com, que é equivalente ao nome de enumeração do caso `AccountStatus`Pascal:.</span><span class="sxs-lookup"><span data-stu-id="a804c-109">For example, in this Protobuf enumeration the fields are prefixed with `ACCOUNT_STATUS`, which is equivalent to the Pascal case enum name: `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="a804c-110">Portanto, o gerador cria um C# equivalente de enum para o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a804c-110">So, the generator creates a C# enum equivalent to the following code:</span></span>

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

<span data-ttu-id="a804c-111">As definições de enumeração Protobuf **devem** ter uma constante zero como seu primeiro campo.</span><span class="sxs-lookup"><span data-stu-id="a804c-111">Protobuf enumeration definitions **must** have a zero constant as their first field.</span></span> <span data-ttu-id="a804c-112">Como no C#, você pode declarar vários campos com o mesmo valor, mas você deve habilitar explicitamente essa opção usando a `allow_alias` opção na enumeração:</span><span class="sxs-lookup"><span data-stu-id="a804c-112">As in C#, you can declare multiple fields with the same value, but you must explicitly enable this option using the `allow_alias` option in the enum:</span></span>

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

<span data-ttu-id="a804c-113">Você pode declarar enumerações no nível superior em um `.proto` arquivo ou aninhado em uma definição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a804c-113">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="a804c-114">Enumerações aninhadas — como mensagens aninhadas — serão declaradas dentro da `.Types` classe estática na classe de mensagem gerada.</span><span class="sxs-lookup"><span data-stu-id="a804c-114">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="a804c-115">Não há como aplicar o atributo [[flags]](xref:System.FlagsAttribute) a uma enumeração gerada por Protobuf, e o Protobuf não compreende combinações de enums de bits.</span><span class="sxs-lookup"><span data-stu-id="a804c-115">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="a804c-116">Veja o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a804c-116">Take a look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

<span data-ttu-id="a804c-117">Se você definir `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`como, ele será serializado como o valor `3`inteiro.</span><span class="sxs-lookup"><span data-stu-id="a804c-117">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="a804c-118">Quando um cliente ou servidor tenta desserializar o valor, ele não encontra uma correspondência na definição de enumeração para `3` e o resultado `Region.None`será.</span><span class="sxs-lookup"><span data-stu-id="a804c-118">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3` and the result will be `Region.None`.</span></span>

<span data-ttu-id="a804c-119">A melhor maneira de trabalhar com vários valores enum em Protobuf é usar um `repeated` campo do tipo enum.</span><span class="sxs-lookup"><span data-stu-id="a804c-119">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a804c-120">[Anterior](protobuf-any-oneof.md)
>[Próximo](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="a804c-120">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>