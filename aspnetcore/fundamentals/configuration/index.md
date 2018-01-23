---
title: "ASP.NET Core의 구성"
author: rick-anderson
description: "구성 API를 사용하여 여러 가지 방법으로 ASP.NET Core 앱을 구성합니다."
manager: wpickett
ms.author: riande
ms.custom: mvc
ms.date: 1/11/2018
ms.topic: article
ms.technology: aspnet
ms.prod: asp.net-core
uid: fundamentals/configuration/index
ms.openlocfilehash: 0f8618898089418f709506aee5eb013f983dc294
ms.sourcegitcommit: 87168cdc409e7a7257f92a0f48f9c5ab320b5b28
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="configure-an-aspnet-core-app"></a><span data-ttu-id="c0c73-103">ASP.NET Core 앱 구성</span><span class="sxs-lookup"><span data-stu-id="c0c73-103">Configure an ASP.NET Core App</span></span>

<span data-ttu-id="c0c73-104">작성자: [Rick Anderson](https://twitter.com/RickAndMSFT), [Mark Michaelis](http://intellitect.com/author/mark-michaelis/), [Steve Smith](https://ardalis.com/), [Daniel Roth](https://github.com/danroth27), [Luke Latham](https://github.com/guardrex)</span><span class="sxs-lookup"><span data-stu-id="c0c73-104">By [Rick Anderson](https://twitter.com/RickAndMSFT), [Mark Michaelis](http://intellitect.com/author/mark-michaelis/), [Steve Smith](https://ardalis.com/), [Daniel Roth](https://github.com/danroth27), and [Luke Latham](https://github.com/guardrex)</span></span>

<span data-ttu-id="c0c73-105">구성 API는 이름-값 쌍 목록을 기반으로 ASP.NET Core 웹앱을 구성하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-105">The Configuration API provides a way to configure an ASP.NET Core web app based on a list of name-value pairs.</span></span> <span data-ttu-id="c0c73-106">구성은 여러 소스에서 런타임에 읽힙니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-106">Configuration is read at runtime from multiple sources.</span></span> <span data-ttu-id="c0c73-107">이러한 이름-값 쌍을 다중 수준 계층으로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-107">You can group these name-value pairs into a multi-level hierarchy.</span></span>

<span data-ttu-id="c0c73-108">다음에 대한 구성 공급자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-108">There are configuration providers for:</span></span>

* <span data-ttu-id="c0c73-109">파일 형식(INI, JSON 및 XML)</span><span class="sxs-lookup"><span data-stu-id="c0c73-109">File formats (INI, JSON, and XML)</span></span>
* <span data-ttu-id="c0c73-110">명령줄 인수</span><span class="sxs-lookup"><span data-stu-id="c0c73-110">Command-line arguments</span></span>
* <span data-ttu-id="c0c73-111">환경 변수</span><span class="sxs-lookup"><span data-stu-id="c0c73-111">Environment variables</span></span>
* <span data-ttu-id="c0c73-112">메모리 내 .NET 개체</span><span class="sxs-lookup"><span data-stu-id="c0c73-112">In-memory .NET objects</span></span>
* <span data-ttu-id="c0c73-113">암호화된 사용자 저장소</span><span class="sxs-lookup"><span data-stu-id="c0c73-113">An encrypted user store</span></span>
* [<span data-ttu-id="c0c73-114">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="c0c73-114">Azure Key Vault</span></span>](xref:security/key-vault-configuration)
* <span data-ttu-id="c0c73-115">사용자 지정 공급자(설치 또는 생성된)</span><span class="sxs-lookup"><span data-stu-id="c0c73-115">Custom providers (installed or created)</span></span>

<span data-ttu-id="c0c73-116">각 구성 값은 문자열 키에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-116">Each configuration value maps to a string key.</span></span> <span data-ttu-id="c0c73-117">설정을 사용자 지정 [POCO](https://wikipedia.org/wiki/Plain_Old_CLR_Object) 개체(속성이 있는 간단한 .NET 클래스)로 deserialize하는 바인딩 지원이 기본적으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-117">There's built-in binding support to deserialize settings into a custom [POCO](https://wikipedia.org/wiki/Plain_Old_CLR_Object) object (a simple .NET class with properties).</span></span>

<span data-ttu-id="c0c73-118">옵션 패턴은 옵션 클래스를 사용하여 관련 설정 그룹을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-118">The options pattern uses options classes to represent groups of related settings.</span></span> <span data-ttu-id="c0c73-119">옵션 패턴 사용에 대한 자세한 내용은 [옵션](xref:fundamentals/configuration/options) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-119">For more information on using the options pattern, see the [Options](xref:fundamentals/configuration/options) topic.</span></span>

<span data-ttu-id="c0c73-120">[샘플 코드 보기 또는 다운로드](https://github.com/aspnet/docs/tree/master/aspnetcore/fundamentals/configuration/index/sample)([다운로드 방법](xref:tutorials/index#how-to-download-a-sample))</span><span class="sxs-lookup"><span data-stu-id="c0c73-120">[View or download sample code](https://github.com/aspnet/docs/tree/master/aspnetcore/fundamentals/configuration/index/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample))</span></span>

## <a name="json-configuration"></a><span data-ttu-id="c0c73-121">JSON 구성</span><span class="sxs-lookup"><span data-stu-id="c0c73-121">JSON configuration</span></span>

<span data-ttu-id="c0c73-122">다음 콘솔 앱은 JSON 구성 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-122">The following console app uses the JSON configuration provider:</span></span>

[!code-csharp[Main](index/sample/ConfigJson/Program.cs)]

<span data-ttu-id="c0c73-123">앱은 다음 구성 설정을 읽고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-123">The app reads and displays the following configuration settings:</span></span>

[!code-json[Main](index/sample/ConfigJson/appsettings.json)]

<span data-ttu-id="c0c73-124">구성은 콜론으로 노드를 구분하는 이름-값 쌍의 계층적 목록으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-124">Configuration consists of a hierarchical list of name-value pairs in which the nodes are separated by a colon.</span></span> <span data-ttu-id="c0c73-125">값을 검색하려면 해당 항목의 키를 사용하여 `Configuration` 인덱서에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-125">To retrieve a value, access the `Configuration` indexer with the corresponding item's key:</span></span>

[!code-csharp[Main](index/sample/ConfigJson/Program.cs?range=24-24)]

<span data-ttu-id="c0c73-126">JSON 형식 구성 소스의 배열을 작업하려면 배열 인덱스를 콜론으로 구분된 문자열의 일부로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-126">To work with arrays in JSON-formatted configuration sources, use an array index as part of the colon-separated string.</span></span> <span data-ttu-id="c0c73-127">다음 예제는 앞에서 나온 `wizards` 배열의 첫 번째 항목 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-127">The following example gets the name of the first item in the preceding `wizards` array:</span></span>

```csharp
Console.Write($"{Configuration["wizards:0:Name"]}");
// Output: Gandalf
```

<span data-ttu-id="c0c73-128">기본 제공 [구성](https://docs.microsoft.com/ dotnet/api/microsoft.extensions.configuration) 공급자에 기록된 이름-값 쌍은 유지되지 **않습니다**.</span><span class="sxs-lookup"><span data-stu-id="c0c73-128">Name-value pairs written to the built-in [Configuration](https://docs.microsoft.com/ dotnet/api/microsoft.extensions.configuration) providers are **not** persisted.</span></span> <span data-ttu-id="c0c73-129">그러나 값을 저장하는 사용자 지정 공급자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-129">However, you can create a custom provider that saves values.</span></span> <span data-ttu-id="c0c73-130">[사용자 지정 구성 공급자](xref:fundamentals/configuration/index#custom-config-providers)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-130">See [custom configuration provider](xref:fundamentals/configuration/index#custom-config-providers).</span></span>

<span data-ttu-id="c0c73-131">이전 샘플은 구성 인덱서를 사용하여 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-131">The preceding sample uses the configuration indexer to read values.</span></span> <span data-ttu-id="c0c73-132">`Startup` 외부에서 구성에 액세스하려면 *옵션 패턴*을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-132">To access configuration outside of `Startup`, use the *options pattern*.</span></span> <span data-ttu-id="c0c73-133">자세한 내용은 [옵션](xref:fundamentals/configuration/options) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-133">For more information, see the [Options](xref:fundamentals/configuration/options) topic.</span></span>


## <a name="configuration-by-environment"></a><span data-ttu-id="c0c73-134">환경별 구성</span><span class="sxs-lookup"><span data-stu-id="c0c73-134">Configuration by environment</span></span>

<span data-ttu-id="c0c73-135">개발, 테스트, 프로덕션 등 환경마다 다른 구성 설정을 사용하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-135">It's typical to have different configuration settings for different environments, for example, development, testing, and production.</span></span> <span data-ttu-id="c0c73-136">ASP.NET Core 2.x 앱의 `CreateDefaultBuilder` 확장 메서드(또는 ASP.NET Core 1.x 앱에서 바로 `AddJsonFile` 및 `AddEnvironmentVariables` 사용)는 JSON 파일 및 시스템 구성 소스를 읽기 위한 구성 공급자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-136">The `CreateDefaultBuilder` extension method in an ASP.NET Core 2.x app (or using `AddJsonFile` and `AddEnvironmentVariables` directly in an ASP.NET Core 1.x app) adds configuration providers for reading JSON files and system configuration sources:</span></span>

* <span data-ttu-id="c0c73-137">*appsettings.json*</span><span class="sxs-lookup"><span data-stu-id="c0c73-137">*appsettings.json*</span></span>
* <span data-ttu-id="c0c73-138">*appsettings.\<EnvironmentName>.json*</span><span class="sxs-lookup"><span data-stu-id="c0c73-138">*appsettings.\<EnvironmentName>.json*</span></span>
* <span data-ttu-id="c0c73-139">환경 변수</span><span class="sxs-lookup"><span data-stu-id="c0c73-139">Environment variables</span></span>

<span data-ttu-id="c0c73-140">ASP.NET Core 1.x 앱은 `AddJsonFile` 및 [AddEnvironmentVariables](https://docs.microsoft.com/ dotnet/api/microsoft.extensions.configuration.environmentvariablesextensions.addenvironmentvariables #Microsoft_Extensions_Configuration_EnvironmentVariablesExtensions_AddEnvironmentVariables_Microsoft_Extensions_Configuration_IConfigurationBuilder_System_String_)를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-140">ASP.NET Core 1.x apps need to call `AddJsonFile` and [AddEnvironmentVariables](https://docs.microsoft.com/ dotnet/api/microsoft.extensions.configuration.environmentvariablesextensions.addenvironmentvariables #Microsoft_Extensions_Configuration_EnvironmentVariablesExtensions_AddEnvironmentVariables_Microsoft_Extensions_Configuration_IConfigurationBuilder_System_String_).</span></span>

<span data-ttu-id="c0c73-141">매개 변수에 대한 설명은 [AddJsonFile](/dotnet/api/microsoft.extensions.configuration.jsonconfigurationextensions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-141">See [AddJsonFile](/dotnet/api/microsoft.extensions.configuration.jsonconfigurationextensions) for an explanation of the parameters.</span></span> <span data-ttu-id="c0c73-142">`reloadOnChange`는 ASP.NET Core 1.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-142">`reloadOnChange` is only supported in ASP.NET Core 1.1 and later.</span></span>

<span data-ttu-id="c0c73-143">구성 소스는 지정된 순서대로 읽힙니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-143">Configuration sources are read in the order that they're specified.</span></span> <span data-ttu-id="c0c73-144">이전 코드에서 환경 변수는 마지막에 읽힙니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-144">In the preceding code, the environment variables are read last.</span></span> <span data-ttu-id="c0c73-145">환경을 통해 설정된 구성 값은 두 이전 공급자에서 설정된 구성 값을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-145">Any configuration values set through the environment replace those set in the two previous providers.</span></span>

<span data-ttu-id="c0c73-146">다음 *appsettings.Staging.json* 파일을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-146">Consider the following *appsettings.Staging.json* file:</span></span>

[!code-json[Main](index/sample/appsettings.Staging.json)]

<span data-ttu-id="c0c73-147">환경이 `Staging`으로 설정되면 다음 `Configure` 메서드가 `MyConfig` 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-147">When the environment is set to `Staging`, the following `Configure` method reads the value of `MyConfig`:</span></span>

[!code-csharp[Main](index/sample/StartupConfig.cs?name=snippet&highlight=3,4)]


<span data-ttu-id="c0c73-148">환경은 일반적으로 `Development`, `Staging` 또는 `Production`으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-148">The environment is typically set to `Development`, `Staging`, or `Production`.</span></span> <span data-ttu-id="c0c73-149">자세한 내용은 [여러 환경 사용](xref:fundamentals/environments)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-149">For more information, see [Working with multiple environments](xref:fundamentals/environments).</span></span>

<span data-ttu-id="c0c73-150">구성 고려 사항:</span><span class="sxs-lookup"><span data-stu-id="c0c73-150">Configuration considerations:</span></span>

* <span data-ttu-id="c0c73-151">`IOptionsSnapshot`은 구성 데이터가 변경되면 구성 데이터를 다시 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-151">`IOptionsSnapshot` can reload configuration data when it changes.</span></span> <span data-ttu-id="c0c73-152">자세한 내용은 [IOptionsSnapshot](xref:fundamentals/configuration/options#reload-configuration-data-with-ioptionssnapshot)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-152">For more information, see [IOptionsSnapshot](xref:fundamentals/configuration/options#reload-configuration-data-with-ioptionssnapshot).,</span></span>
* <span data-ttu-id="c0c73-153">구성 키는 대/소문자를 구분하지 **않습니다**.</span><span class="sxs-lookup"><span data-stu-id="c0c73-153">Configuration keys are **not** case-sensitive.</span></span>
* <span data-ttu-id="c0c73-154">구성 공급자 코드 또는 일반 텍스트 구성 파일에 암호 또는 기타 중요한 데이터를 **절대 저장하지 마세요**.</span><span class="sxs-lookup"><span data-stu-id="c0c73-154">**Never** store passwords or other sensitive data in configuration provider code or in plain text configuration files.</span></span> <span data-ttu-id="c0c73-155">개발 또는 테스트 환경에서 프로덕션 비밀을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-155">Don't use production secrets in your development or test environments.</span></span> <span data-ttu-id="c0c73-156">의도치 않게 리포지토리에 커밋되는 일이 없도록 프로젝트 외부에서 비밀을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-156">Specify secrets outside of the project so that they can't be accidentally committed to your repository.</span></span> <span data-ttu-id="c0c73-157">[여러 환경 사용](xref:fundamentals/environments) 및 [개발 중 안전한 앱 비밀 저장소](xref:security/app-secrets) 관리에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-157">Learn more about [working with multiple environments](xref:fundamentals/environments) and managing [safe storage of app secrets during development](xref:security/app-secrets).</span></span>
* <span data-ttu-id="c0c73-158">시스템의 환경 변수에서 콜론(`:`)을 사용할 수 없으면 콜론(`:`)을 이중 밑줄(`__`)로 바꾸세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-158">If a colon (`:`) can't be used in environment variables on your system, replace the colon (`:`) with a double-underscore (`__`).</span></span>

## <a name="in-memory-provider-and-binding-to-a-poco-class"></a><span data-ttu-id="c0c73-159">메모리 내 공급자 및 POCO 클래스에 바인딩</span><span class="sxs-lookup"><span data-stu-id="c0c73-159">In-memory provider and binding to a POCO class</span></span>

<span data-ttu-id="c0c73-160">다음 샘플은 메모리 내 공급자를 사용하고 클래스에 바인딩하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-160">The following sample shows how to use the in-memory provider and bind to a class:</span></span>

[!code-csharp[Main](index/sample/InMemory/Program.cs)]

<span data-ttu-id="c0c73-161">구성 값이 문자열로 반환되지만, 바인딩을 통해 개체를 생성할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-161">Configuration values are returned as strings, but binding enables the construction of objects.</span></span> <span data-ttu-id="c0c73-162">바인딩을 사용하면 POCO 개체 또는 심지어 전체 개체 그래프를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-162">Binding allows you to retrieve POCO objects or even entire object graphs.</span></span>

### <a name="getvalue"></a><span data-ttu-id="c0c73-163">GetValue</span><span class="sxs-lookup"><span data-stu-id="c0c73-163">GetValue</span></span>

<span data-ttu-id="c0c73-164">다음 샘플은 [GetValue&lt;T&gt;](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.configuration.configurationbinder#Microsoft_Extensions_Configuration_ConfigurationBinder_GetValue_Microsoft_Extensions_Configuration_IConfiguration_System_Type_System_String_System_Object_) 확장 메서드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-164">The following sample demonstrates the [GetValue&lt;T&gt;](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.configuration.configurationbinder#Microsoft_Extensions_Configuration_ConfigurationBinder_GetValue_Microsoft_Extensions_Configuration_IConfiguration_System_Type_System_String_System_Object_) extension method:</span></span>

[!code-csharp[Main](index/sample/InMemoryGetValue/Program.cs?highlight=31)]

<span data-ttu-id="c0c73-165">ConfigurationBinder의 `GetValue<T>` 메서드를 사용하여 기본값을 지정할 수 있습니다(이 샘플에서는 80).</span><span class="sxs-lookup"><span data-stu-id="c0c73-165">The ConfigurationBinder's `GetValue<T>` method allows you to specify a default value (80 in the sample).</span></span> <span data-ttu-id="c0c73-166">`GetValue<T>`는 간단한 시나리오에 사용되며 전체 섹션에 바인딩되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-166">`GetValue<T>` is for simple scenarios and does not bind to entire sections.</span></span> <span data-ttu-id="c0c73-167">`GetValue<T>`는 특정 형식으로 변환된 `GetSection(key).Value`에서 스칼라 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-167">`GetValue<T>` gets scalar values from `GetSection(key).Value` converted to a specific type.</span></span>

## <a name="bind-to-an-object-graph"></a><span data-ttu-id="c0c73-168">개체 그래프에 바인딩</span><span class="sxs-lookup"><span data-stu-id="c0c73-168">Bind to an object graph</span></span>

<span data-ttu-id="c0c73-169">클래스의 각 개체에 재귀적으로 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-169">You can recursively bind to each object in a class.</span></span> <span data-ttu-id="c0c73-170">다음 `AppSettings` 클래스를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-170">Consider the following `AppSettings` class:</span></span>

[!code-csharp[Main](index/sample/ObjectGraph/AppSettings.cs)]

<span data-ttu-id="c0c73-171">다음 샘플은 `AppSettings` 클래스에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-171">The following sample binds to the `AppSettings` class:</span></span>

[!code-csharp[Main](index/sample/ObjectGraph/Program.cs?highlight=15-16)]

<span data-ttu-id="c0c73-172">**ASP.NET Core 1.1** 이상은 전체 섹션에서 작동하는 `Get<T>`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-172">**ASP.NET Core 1.1** and higher can use `Get<T>`, which works with entire sections.</span></span> <span data-ttu-id="c0c73-173">`Get<T>`가 `Bind`을 사용하는 것보다 편리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-173">`Get<T>` can be more convenient than using `Bind`.</span></span> <span data-ttu-id="c0c73-174">다음 코드는 이전 샘플에 `Get<T>`를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-174">The following code shows how to use `Get<T>` with the preceding sample:</span></span>

```csharp
var appConfig = config.GetSection("App").Get<AppSettings>();
```

<span data-ttu-id="c0c73-175">다음 *appsettings.json* 파일 사용:</span><span class="sxs-lookup"><span data-stu-id="c0c73-175">Using the following *appsettings.json* file:</span></span>

[!code-json[Main](index/sample/ObjectGraph/appsettings.json)]

<span data-ttu-id="c0c73-176">프로그램에서는 `Height 11`을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-176">The program displays `Height 11`.</span></span>

<span data-ttu-id="c0c73-177">다음 코드를 구성 단위 테스트에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-177">The following code can be used to unit test the configuration:</span></span>

```csharp
[Fact]
public void CanBindObjectTree()
{
    var dict = new Dictionary<string, string>
        {
            {"App:Profile:Machine", "Rick"},
            {"App:Connection:Value", "connectionstring"},
            {"App:Window:Height", "11"},
            {"App:Window:Width", "11"}
        };
    var builder = new ConfigurationBuilder();
    builder.AddInMemoryCollection(dict);
    var config = builder.Build();

    var settings = new AppSettings();
    config.GetSection("App").Bind(settings);

    Assert.Equal("Rick", settings.Profile.Machine);
    Assert.Equal(11, settings.Window.Height);
    Assert.Equal(11, settings.Window.Width);
    Assert.Equal("connectionstring", settings.Connection.Value);
}
```

<a name="custom-config-providers"></a>

## <a name="create-an-entity-framework-custom-provider"></a><span data-ttu-id="c0c73-178">Entity Framework 사용자 지정 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="c0c73-178">Create an Entity Framework custom provider</span></span>

<span data-ttu-id="c0c73-179">이 섹션에서는 EF를 사용하여 데이터베이스에서 이름-값 쌍을 읽는 기본 구성 공급자가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-179">In this section, a basic configuration provider that reads name-value pairs from a database using EF is created.</span></span>

<span data-ttu-id="c0c73-180">데이터베이스에 구성 값을 저장하는 `ConfigurationValue` 엔터티를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-180">Define a `ConfigurationValue` entity for storing configuration values in the database:</span></span>

[!code-csharp[Main](index/sample/CustomConfigurationProvider/ConfigurationValue.cs)]

<span data-ttu-id="c0c73-181">구성된 값을 저장 및 액세스하는 `ConfigurationContext`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-181">Add a `ConfigurationContext` to store and access the configured values:</span></span>

[!code-csharp[Main](index/sample/CustomConfigurationProvider/ConfigurationContext.cs?name=snippet1)]

<span data-ttu-id="c0c73-182">[IConfigurationSource](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.configuration.iconfigurationsource)를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-182">Create a class that implements [IConfigurationSource](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.configuration.iconfigurationsource):</span></span>

[!code-csharp[Main](index/sample/CustomConfigurationProvider/EntityFrameworkConfigurationSource.cs?highlight=7)]

<span data-ttu-id="c0c73-183">[ConfigurationProvider](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.configuration.configurationprovider)에서 상속하여 사용자 지정 구성 공급자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-183">Create the custom configuration provider by inheriting from [ConfigurationProvider](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.configuration.configurationprovider).</span></span> <span data-ttu-id="c0c73-184">구성 공급자는 비어 있는 데이터베이스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-184">The configuration provider initializes the database when it's empty:</span></span>

[!code-csharp[Main](index/sample/CustomConfigurationProvider/EntityFrameworkConfigurationProvider.cs?highlight=9,18-31,38-39)]

<span data-ttu-id="c0c73-185">샘플이 실행되면 데이터베이스의 강조 표시된 값("value_from_ef_1" 및 "value_from_ef_2")이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-185">The highlighted values from the database ("value_from_ef_1" and "value_from_ef_2") are displayed when the sample is run.</span></span>

<span data-ttu-id="c0c73-186">구성 소스를 추가하기 위한 `EFConfigSource` 확장 메서드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-186">You can add an `EFConfigSource` extension method for adding the configuration source:</span></span>

[!code-csharp[Main](index/sample/CustomConfigurationProvider/EntityFrameworkExtensions.cs?highlight=12)]

<span data-ttu-id="c0c73-187">다음 코드는 사용자 지정 `EFConfigProvider`를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-187">The following code shows how to use the custom `EFConfigProvider`:</span></span>

[!code-csharp[Main](index/sample/CustomConfigurationProvider/Program.cs?highlight=21-26)]

<span data-ttu-id="c0c73-188">이 샘플은 JSON 공급자 뒤에 사용자 지정 `EFConfigProvider`를 추가하므로 데이터베이스의 모든 설정이 *appsettings.json* 파일의 설정을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-188">Note the sample adds the custom `EFConfigProvider` after the JSON provider, so any settings from the database will override settings from the *appsettings.json* file.</span></span>

<span data-ttu-id="c0c73-189">다음 *appsettings.json* 파일 사용:</span><span class="sxs-lookup"><span data-stu-id="c0c73-189">Using the following *appsettings.json* file:</span></span>

[!code-json[Main](index/sample/CustomConfigurationProvider/appsettings.json)]

<span data-ttu-id="c0c73-190">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-190">The following output is displayed:</span></span>

```console
key1=value_from_ef_1
key2=value_from_ef_2
key3=value_from_json_3
```

## <a name="commandline-configuration-provider"></a><span data-ttu-id="c0c73-191">CommandLine 구성 공급자</span><span class="sxs-lookup"><span data-stu-id="c0c73-191">CommandLine configuration provider</span></span>

<span data-ttu-id="c0c73-192">[CommandLine 구성 공급자](/aspnet/core/api/microsoft.extensions.configuration.commandline.commandlineconfigurationprovider)는 런타임에 구성에 대한 명령줄 인수 키-값 쌍을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-192">The [CommandLine configuration provider](/aspnet/core/api/microsoft.extensions.configuration.commandline.commandlineconfigurationprovider) receives command-line argument key-value pairs for configuration at runtime.</span></span>

[<span data-ttu-id="c0c73-193">CommandLine 구성 샘플 살펴보기 또는 다운로드</span><span class="sxs-lookup"><span data-stu-id="c0c73-193">View or download the CommandLine configuration sample</span></span>](https://github.com/aspnet/docs/tree/master/aspnetcore/fundamentals/index/sample/CommandLine)

### <a name="setup-and-use-the-commandline-configuration-provider"></a><span data-ttu-id="c0c73-194">CommandLine 구성 공급자 설정 및 사용</span><span class="sxs-lookup"><span data-stu-id="c0c73-194">Setup and use the CommandLine configuration provider</span></span>

# <a name="basic-configurationtabbasicconfiguration"></a>[<span data-ttu-id="c0c73-195">기본 구성</span><span class="sxs-lookup"><span data-stu-id="c0c73-195">Basic Configuration</span></span>](#tab/basicconfiguration)

<span data-ttu-id="c0c73-196">명령줄 구성을 활성화하려면 [ConfigurationBuilder](/api/microsoft.extensions.configuration.configurationbuilder) 인스턴스에서 `AddCommandLine` 확장 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-196">To activate command-line configuration, call the `AddCommandLine` extension method on an instance of [ConfigurationBuilder](/api/microsoft.extensions.configuration.configurationbuilder):</span></span>

[!code-csharp[Main](index/sample_snapshot//CommandLine/Program.cs?highlight=18,21)]

<span data-ttu-id="c0c73-197">코드를 실행하면 다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-197">Running the code, the following output is displayed:</span></span>

```console
MachineName: MairaPC
Left: 1980
```

<span data-ttu-id="c0c73-198">명령줄에서 인수 키-값 쌍을 전달하면 `Profile:MachineName` 및 `App:MainWindow:Left` 값이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-198">Passing argument key-value pairs on the command line changes the values of `Profile:MachineName` and `App:MainWindow:Left`:</span></span>

```console
dotnet run Profile:MachineName=BartPC App:MainWindow:Left=1979
```

<span data-ttu-id="c0c73-199">콘솔 창에 다음 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-199">The console window displays:</span></span>

```console
MachineName: BartPC
Left: 1979
```

<span data-ttu-id="c0c73-200">다른 구성 공급자가 제공한 구성을 명령줄 구성으로 재정의하려면 `ConfigurationBuilder`의 마지막에서 `AddCommandLine`을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-200">To override configuration provided by other configuration providers with command-line configuration, call `AddCommandLine` last on `ConfigurationBuilder`:</span></span>

[!code-csharp[Main](index/sample_snapshot//CommandLine/Program2.cs?range=11-16&highlight=1,5)]

# <a name="aspnet-core-2xtabaspnetcore2x"></a>[<span data-ttu-id="c0c73-201">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c0c73-201">ASP.NET Core 2.x</span></span>](#tab/aspnetcore2x)

<span data-ttu-id="c0c73-202">일반적인 ASP.NET Core 2.x 앱은 고정적인 편의 메서드를 사용하여 `CreateDefaultBuilder`를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-202">Typical ASP.NET Core 2.x apps use the static convenience method `CreateDefaultBuilder` to build the host:</span></span>

[!code-csharp[Main](index/sample_snapshot//Program.cs?highlight=12)]

<span data-ttu-id="c0c73-203">`CreateDefaultBuilder`는 *appsettings.json*, *appsettings.{Environment}.json*, [사용자 비밀](xref:security/app-secrets)(`Development` 환경의 경우), 환경 변수 및 명령줄 인수에서 선택적 구성을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-203">`CreateDefaultBuilder` loads optional configuration from *appsettings.json*, *appsettings.{Environment}.json*, [user secrets](xref:security/app-secrets) (in the `Development` environment), environment variables, and command-line arguments.</span></span> <span data-ttu-id="c0c73-204">CommandLine 구성 공급자는 마지막에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-204">The CommandLine configuration provider is called last.</span></span> <span data-ttu-id="c0c73-205">공급자가 마지막에 호출되기 때문에 다른 구성 공급자가 이전에 설정한 구성을 런타임에 전달되는 명령줄 인수가 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-205">Calling the provider last allows the command-line arguments passed at runtime to override configuration set by the other configuration providers called earlier.</span></span>

<span data-ttu-id="c0c73-206">*appsettings* 파일에는</span><span class="sxs-lookup"><span data-stu-id="c0c73-206">For *appsettings* files where:</span></span>

* <span data-ttu-id="c0c73-207">`reloadOnChange`가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-207">`reloadOnChange` is enabled.</span></span>
* <span data-ttu-id="c0c73-208">명령줄 인수와 *appsettings* 파일에 동일한 설정을 포함하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-208">Contain the same setting in the command-line arguments and an *appsettings* file.</span></span>
* <span data-ttu-id="c0c73-209">일치하는 명령줄 인수가 포함된 *appsettings* 파일은 앱이 시작된 후 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-209">The *appsettings* file containing the matching command-line argument is changed after the app starts.</span></span>

<span data-ttu-id="c0c73-210">이전 조건이 모두 참인 경우 명령줄 인수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-210">If all the preceding conditions are true, the command-line arguments are overridden.</span></span>

<span data-ttu-id="c0c73-211">ASP.NET Core 2.x 앱은 [ConfigurationBuilder](/api/microsoft.extensions.configuration.configurationbuilder)를 사용하여 수동으로 설정된 구성인 \`\`CreateDefaultBuilder`. When using `WebHostBuilder\` 대신 WebHostBuilder](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilder)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-211">ASP.NET Core 2.x app can use WebHostBuilder](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilder) instead of \`\`CreateDefaultBuilder`. When using `WebHostBuilder\`, manually set configuration with [ConfigurationBuilder](/api/microsoft.extensions.configuration.configurationbuilder).</span></span> <span data-ttu-id="c0c73-212">자세한 내용은 ASP.NET Core 1.x 탭을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-212">See the ASP.NET Core 1.x tab for more information.</span></span>

# <a name="aspnet-core-1xtabaspnetcore1x"></a>[<span data-ttu-id="c0c73-213">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c0c73-213">ASP.NET Core 1.x</span></span>](#tab/aspnetcore1x)

<span data-ttu-id="c0c73-214">[ConfigurationBuilder](/api/microsoft.extensions.configuration.configurationbuilder)를 만들고 `AddCommandLine` 메서드를 호출하여 CommandLine 구성 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-214">Create a [ConfigurationBuilder](/api/microsoft.extensions.configuration.configurationbuilder) and call the `AddCommandLine` method to use the CommandLine configuration provider.</span></span> <span data-ttu-id="c0c73-215">공급자가 마지막에 호출되기 때문에 다른 구성 공급자가 이전에 설정한 구성을 런타임에 전달되는 명령줄 인수가 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-215">Calling the provider last allows the command-line arguments passed at runtime to override configuration set by the other configuration providers called earlier.</span></span> <span data-ttu-id="c0c73-216">`UseConfiguration` 메서드를 사용하여 [WebHostBuilder](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilder)에 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-216">Apply the configuration to [WebHostBuilder](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilder) with the `UseConfiguration` method:</span></span>

[!code-csharp[Main](index/sample_snapshot//CommandLine/Program2.cs?highlight=11,15,19)]

---

### <a name="arguments"></a><span data-ttu-id="c0c73-217">인수</span><span class="sxs-lookup"><span data-stu-id="c0c73-217">Arguments</span></span>

<span data-ttu-id="c0c73-218">명령줄에 전달된 인수는 다음 표에 표시된 두 형식 중 하나를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-218">Arguments passed on the command line must conform to one of two formats shown in the following table:</span></span>

| <span data-ttu-id="c0c73-219">인수 형식</span><span class="sxs-lookup"><span data-stu-id="c0c73-219">Argument format</span></span>                                                     | <span data-ttu-id="c0c73-220">예</span><span class="sxs-lookup"><span data-stu-id="c0c73-220">Example</span></span>        |
| ------------------------------------------------------------------- | :------------: |
| <span data-ttu-id="c0c73-221">단일 인수: 등호로 구분되는 키-값 쌍(`=`)</span><span class="sxs-lookup"><span data-stu-id="c0c73-221">Single argument: a key-value pair separated by an equals sign (`=`)</span></span> | `key1=value`   |
| <span data-ttu-id="c0c73-222">두 인수 시퀀스: 공백으로 구분되는 키-값 쌍</span><span class="sxs-lookup"><span data-stu-id="c0c73-222">Sequence of two arguments: a key-value pair separated by a space</span></span>    | `/key1 value1` |

<span data-ttu-id="c0c73-223">**단일 인수**</span><span class="sxs-lookup"><span data-stu-id="c0c73-223">**Single argument**</span></span>

<span data-ttu-id="c0c73-224">값이 등호를 따라야 합니다(`=`).</span><span class="sxs-lookup"><span data-stu-id="c0c73-224">The value must follow an equals sign (`=`).</span></span> <span data-ttu-id="c0c73-225">값이 null일 수 있습니다(예: `mykey=`).</span><span class="sxs-lookup"><span data-stu-id="c0c73-225">The value can be null (for example, `mykey=`).</span></span>

<span data-ttu-id="c0c73-226">키에 접두사가 붙을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-226">The key may have a prefix.</span></span>

| <span data-ttu-id="c0c73-227">키 접두사</span><span class="sxs-lookup"><span data-stu-id="c0c73-227">Key prefix</span></span>               | <span data-ttu-id="c0c73-228">예</span><span class="sxs-lookup"><span data-stu-id="c0c73-228">Example</span></span>         |
| ------------------------ | :-------------: |
| <span data-ttu-id="c0c73-229">접두사 없음</span><span class="sxs-lookup"><span data-stu-id="c0c73-229">No prefix</span></span>                | `key1=value1`   |
| <span data-ttu-id="c0c73-230">단일 대시(`-`)&#8224;</span><span class="sxs-lookup"><span data-stu-id="c0c73-230">Single dash (`-`)&#8224;</span></span> | `-key2=value2`  |
| <span data-ttu-id="c0c73-231">대시 2개(`--`)</span><span class="sxs-lookup"><span data-stu-id="c0c73-231">Two dashes (`--`)</span></span>        | `--key3=value3` |
| <span data-ttu-id="c0c73-232">슬래시(`/`)</span><span class="sxs-lookup"><span data-stu-id="c0c73-232">Forward slash (`/`)</span></span>      | `/key4=value4`  |

<span data-ttu-id="c0c73-233">&#8224;단일 대시 접두사(`-`)가 붙은 키는 아래에 설명된 [스위치 매핑](#switch-mappings)에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-233">&#8224;A key with a single dash prefix (`-`) must be provided in [switch mappings](#switch-mappings), described below.</span></span>

<span data-ttu-id="c0c73-234">예제 명령:</span><span class="sxs-lookup"><span data-stu-id="c0c73-234">Example command:</span></span>

```console
dotnet run key1=value1 -key2=value2 --key3=value3 /key4=value4
```

<span data-ttu-id="c0c73-235">참고: 구성 공급자에게 제공된 [스위치 매핑](#switch-mappings)에 `-key1`가 없으면 `FormatException`이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-235">Note: If `-key1` isn't present in the [switch mappings](#switch-mappings) given to the configuration provider, a `FormatException` is thrown.</span></span>

<span data-ttu-id="c0c73-236">**두 인수 시퀀스**</span><span class="sxs-lookup"><span data-stu-id="c0c73-236">**Sequence of two arguments**</span></span>

<span data-ttu-id="c0c73-237">값이 null일 수 없으며 공백으로 구분되는 키를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-237">The value can't be null and must follow the key separated by a space.</span></span>

<span data-ttu-id="c0c73-238">키에 접두사가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-238">The key must have a prefix.</span></span>

| <span data-ttu-id="c0c73-239">키 접두사</span><span class="sxs-lookup"><span data-stu-id="c0c73-239">Key prefix</span></span>               | <span data-ttu-id="c0c73-240">예</span><span class="sxs-lookup"><span data-stu-id="c0c73-240">Example</span></span>         |
| ------------------------ | :-------------: |
| <span data-ttu-id="c0c73-241">단일 대시(`-`)&#8224;</span><span class="sxs-lookup"><span data-stu-id="c0c73-241">Single dash (`-`)&#8224;</span></span> | `-key1 value1`  |
| <span data-ttu-id="c0c73-242">대시 2개(`--`)</span><span class="sxs-lookup"><span data-stu-id="c0c73-242">Two dashes (`--`)</span></span>        | `--key2 value2` |
| <span data-ttu-id="c0c73-243">슬래시(`/`)</span><span class="sxs-lookup"><span data-stu-id="c0c73-243">Forward slash (`/`)</span></span>      | `/key3 value3`  |

<span data-ttu-id="c0c73-244">&#8224;단일 대시 접두사(`-`)가 붙은 키는 아래에 설명된 [스위치 매핑](#switch-mappings)에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-244">&#8224;A key with a single dash prefix (`-`) must be provided in [switch mappings](#switch-mappings), described below.</span></span>

<span data-ttu-id="c0c73-245">예제 명령:</span><span class="sxs-lookup"><span data-stu-id="c0c73-245">Example command:</span></span>

```console
dotnet run -key1 value1 --key2 value2 /key3 value3
```

<span data-ttu-id="c0c73-246">참고: 구성 공급자에게 제공된 [스위치 매핑](#switch-mappings)에 `-key1`가 없으면 `FormatException`이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-246">Note: If `-key1` isn't present in the [switch mappings](#switch-mappings) given to the configuration provider, a `FormatException` is thrown.</span></span>

### <a name="duplicate-keys"></a><span data-ttu-id="c0c73-247">중복 키</span><span class="sxs-lookup"><span data-stu-id="c0c73-247">Duplicate keys</span></span>

<span data-ttu-id="c0c73-248">중복 키를 제공하면 마지막 키-값 쌍이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-248">If duplicate keys are provided, the last key-value pair is used.</span></span>

### <a name="switch-mappings"></a><span data-ttu-id="c0c73-249">스위치 매핑</span><span class="sxs-lookup"><span data-stu-id="c0c73-249">Switch mappings</span></span>

<span data-ttu-id="c0c73-250">`ConfigurationBuilder`를 사용하여 수동으로 구성을 빌드하는 경우 선택적으로 `AddCommandLine` 메서드에 스위치 매핑 사전을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-250">When manually building configuration with `ConfigurationBuilder`, you can optionally provide a switch mappings dictionary to the `AddCommandLine` method.</span></span> <span data-ttu-id="c0c73-251">스위치 매핑을 통해 키 이름 교체 논리를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-251">Switch mappings allow you to provide key name replacement logic.</span></span>

<span data-ttu-id="c0c73-252">스위치 매핑 사전을 사용하면 명령줄 인수를 통해 제공된 키와 일치하는 키에 대해 사전을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-252">When the switch mappings dictionary is used, the dictionary is checked for a key that matches the key provided by a command-line argument.</span></span> <span data-ttu-id="c0c73-253">사전에서 명령줄 키가 발견되면 사전 값(키 교체)이 다시 구성으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-253">If the command-line key is found in the dictionary, the dictionary value (the key replacement) is passed back to set the configuration.</span></span> <span data-ttu-id="c0c73-254">단일 대시(`-`) 접두사가 붙은 명령줄 키에는 스위치 매핑이 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-254">A switch mapping is required for any command-line key prefixed with a single dash (`-`).</span></span>

<span data-ttu-id="c0c73-255">스위치 매핑 사전 키 규칙:</span><span class="sxs-lookup"><span data-stu-id="c0c73-255">Switch mappings dictionary key rules:</span></span>

* <span data-ttu-id="c0c73-256">스위치는 단일 대시(`-`) 또는 이중 대시(`--`)로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-256">Switches must start with a dash (`-`) or double-dash (`--`).</span></span>
* <span data-ttu-id="c0c73-257">스위치 매핑 사전이 중복 키를 포함하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-257">The switch mappings dictionary must not contain duplicate keys.</span></span>

<span data-ttu-id="c0c73-258">다음 예제의 `GetSwitchMappings` 메서드는 명령줄 인수가 단일 대시(`-`) 키 접두사를 사용하고 선행 하위 키 접두사를 사용하지 않는 것을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-258">In the following example, the `GetSwitchMappings` method allows your command-line arguments to use a single dash (`-`) key prefix and avoid leading subkey prefixes.</span></span>

[!code-csharp[Main](index/sample/CommandLine/Program.cs?highlight=10-19,32)]

<span data-ttu-id="c0c73-259">`AddInMemoryCollection`에 제공된 사전은 명령줄 인수를 제공하지 않고 구성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-259">Without providing command-line arguments, the dictionary provided to `AddInMemoryCollection` sets the configuration values.</span></span> <span data-ttu-id="c0c73-260">다음 명령을 사용하여 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-260">Run the app with the following command:</span></span>

```console
dotnet run
```

<span data-ttu-id="c0c73-261">콘솔 창에 다음 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-261">The console window displays:</span></span>

```console
MachineName: RickPC
Left: 1980
```

<span data-ttu-id="c0c73-262">다음 명령을 사용하여 구성 설정을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-262">Use the following to pass in configuration settings:</span></span>

```console
dotnet run /Profile:MachineName=DahliaPC /App:MainWindow:Left=1984
```

<span data-ttu-id="c0c73-263">콘솔 창에 다음 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-263">The console window displays:</span></span>

```console
MachineName: DahliaPC
Left: 1984
```

<span data-ttu-id="c0c73-264">생성된 스위치 매핑 사전은 다음 표의 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-264">After the switch mappings dictionary is created, it contains the data shown in the following table:</span></span>

| <span data-ttu-id="c0c73-265">Key</span><span class="sxs-lookup"><span data-stu-id="c0c73-265">Key</span></span>            | <span data-ttu-id="c0c73-266">값</span><span class="sxs-lookup"><span data-stu-id="c0c73-266">Value</span></span>                 |
| -------------- | --------------------- |
| `-MachineName` | `Profile:MachineName` |
| `-Left`        | `App:MainWindow:Left` |

<span data-ttu-id="c0c73-267">사전을 사용하여 키 전환을 보여 주려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-267">To demonstrate key switching using the dictionary, run the following command:</span></span>

```console
dotnet run -MachineName=ChadPC -Left=1988
```

<span data-ttu-id="c0c73-268">명령줄 키가 교환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-268">The command-line keys are swapped.</span></span> <span data-ttu-id="c0c73-269">콘솔 창에 `Profile:MachineName` 및 `App:MainWindow:Left`의 구성 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-269">The console window displays the configuration values for `Profile:MachineName` and `App:MainWindow:Left`:</span></span>

```console
MachineName: ChadPC
Left: 1988
```

## <a name="the-webconfig-file"></a><span data-ttu-id="c0c73-270">web.config 파일</span><span class="sxs-lookup"><span data-stu-id="c0c73-270">The web.config file</span></span>

<span data-ttu-id="c0c73-271">IIS 또는 IIS Express에서 앱을 호스트하는 경우 *web.config* 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-271">A *web.config* file is required when hosting the app in IIS or IIS Express.</span></span> <span data-ttu-id="c0c73-272">*web.config*의 설정은 IIS의 [ASP.NET Core Module](xref:fundamentals/servers/aspnet-core-module)이 앱을 시작하고 다른 IIS 설정 및 모듈을 구성할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-272">Settings in *web.config* enable the [ASP.NET Core Module](xref:fundamentals/servers/aspnet-core-module) to launch the app and configure other IIS settings and modules.</span></span> <span data-ttu-id="c0c73-273">*web.config* 파일이 없고 프로젝트 파일에 `<Project Sdk="Microsoft.NET.Sdk.Web">`이 포함되어 있는 경우 프로젝트를 게시하면 게시된 출력에 *web.config* 파일이 만들어집니다(*게시* 폴더).</span><span class="sxs-lookup"><span data-stu-id="c0c73-273">If the *web.config* file isn't present and the project file includes `<Project Sdk="Microsoft.NET.Sdk.Web">`, publishing the project creates a *web.config* file in the published output (the *publish* folder).</span></span> <span data-ttu-id="c0c73-274">자세한 내용은 [IIS가 있는 Windows에서 ASP.NET Core 호스팅](xref:host-and-deploy/iis/index#webconfig)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-274">For more information, see [Host ASP.NET Core on Windows with IIS](xref:host-and-deploy/iis/index#webconfig).</span></span>

## <a name="additional-notes"></a><span data-ttu-id="c0c73-275">추가 참고 사항</span><span class="sxs-lookup"><span data-stu-id="c0c73-275">Additional notes</span></span>

* <span data-ttu-id="c0c73-276">`ConfigureServices`가 호출되기 전에는 DI(종속성 주입)가 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-276">Dependency Injection (DI) is not set up until after `ConfigureServices` is invoked.</span></span>
* <span data-ttu-id="c0c73-277">구성 시스템에서 DI를 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-277">The configuration system is not DI aware.</span></span>
* <span data-ttu-id="c0c73-278">`IConfiguration`에는 두 가지 특수화가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-278">`IConfiguration` has two specializations:</span></span>
  * <span data-ttu-id="c0c73-279">`IConfigurationRoot`는 루트 노드에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-279">`IConfigurationRoot` Used for the root node.</span></span> <span data-ttu-id="c0c73-280">다시 로드를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-280">Can trigger a reload.</span></span>
  * <span data-ttu-id="c0c73-281">`IConfigurationSection`은 구성 값의 섹션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-281">`IConfigurationSection` Represents a section of configuration values.</span></span> <span data-ttu-id="c0c73-282">`GetSection` 및 `GetChildren` 메서드는 `IConfigurationSection`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-282">The `GetSection` and `GetChildren` methods return an `IConfigurationSection`.</span></span>
  * <span data-ttu-id="c0c73-283">구성을 다시 로드하는 경우 또는 각 공급자에 액세스해야 하는 경우 [IConfigurationRoot](https://docs.microsoft.com/ dotnet/api/microsoft.extensions.configuration.iconfigurationroot)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c73-283">Use [IConfigurationRoot](https://docs.microsoft.com/ dotnet/api/microsoft.extensions.configuration.iconfigurationroot) when reloading configuration or need access to each provider.</span></span> <span data-ttu-id="c0c73-284">이러한 상황은 일반적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c73-284">Neither of these situations are common.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c0c73-285">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="c0c73-285">Additional resources</span></span>

* [<span data-ttu-id="c0c73-286">옵션</span><span class="sxs-lookup"><span data-stu-id="c0c73-286">Options</span></span>](xref:fundamentals/configuration/options)
* [<span data-ttu-id="c0c73-287">여러 환경 사용</span><span class="sxs-lookup"><span data-stu-id="c0c73-287">Working with Multiple Environments</span></span>](xref:fundamentals/environments)
* [<span data-ttu-id="c0c73-288">개발 중 안전한 앱 비밀 저장소</span><span class="sxs-lookup"><span data-stu-id="c0c73-288">Safe storage of app secrets during development</span></span>](xref:security/app-secrets)
* [<span data-ttu-id="c0c73-289">ASP.NET Core에서 호스팅</span><span class="sxs-lookup"><span data-stu-id="c0c73-289">Hosting in ASP.NET Core</span></span>](xref:fundamentals/hosting)
* [<span data-ttu-id="c0c73-290">종속성 주입</span><span class="sxs-lookup"><span data-stu-id="c0c73-290">Dependency Injection</span></span>](xref:fundamentals/dependency-injection)
* [<span data-ttu-id="c0c73-291">Azure Key Vault 구성 공급자</span><span class="sxs-lookup"><span data-stu-id="c0c73-291">Azure Key Vault configuration provider</span></span>](xref:security/key-vault-configuration)