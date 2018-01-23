---
title: "ASP.NET Core의 razor 페이지 권한 부여 규칙"
author: guardrex
description: "시작 시 사용자가 권한을 부여 하 고 익명 사용자가 개별 페이지나 페이지의 하위 폴더에 액세스할 수 있도록 하는 규칙을 사용 하 여 페이지에 대 한 액세스를 제어 하는 방법에 알아봅니다."
ms.author: riande
manager: wpickett
ms.date: 10/27/2017
ms.topic: article
ms.technology: aspnet
ms.prod: asp.net-core
uid: security/authorization/razor-pages-authorization
ms.openlocfilehash: 72b558816e687c30d0c60f2fd85227d0d803219b
ms.sourcegitcommit: 3e303620a125325bb9abd4b2d315c106fb8c47fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2018
---
# <a name="razor-pages-authorization-conventions-in-aspnet-core"></a><span data-ttu-id="1f263-103">ASP.NET Core의 razor 페이지 권한 부여 규칙</span><span class="sxs-lookup"><span data-stu-id="1f263-103">Razor Pages authorization conventions in ASP.NET Core</span></span>

<span data-ttu-id="1f263-104">[Luke Latham](https://github.com/guardrex)으로</span><span class="sxs-lookup"><span data-stu-id="1f263-104">By [Luke Latham](https://github.com/guardrex)</span></span>

<span data-ttu-id="1f263-105">Razor 페이지 응용 프로그램에서 액세스를 제어 하는 한 가지 방법은 시작 시 권한 부여 규칙을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-105">One way to control access in your Razor Pages app is to use authorization conventions at startup.</span></span> <span data-ttu-id="1f263-106">이러한 규칙을 사용 하 여 사용자 권한을 부여 하 고 익명 사용자가 개별 페이지나 페이지의 하위 폴더에 액세스할 수 있도록 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-106">These conventions allow you to authorize users and allow anonymous users to access individual pages or folders of pages.</span></span> <span data-ttu-id="1f263-107">자동으로이 항목에서 설명 하는 규칙이 적용 [권한 부여 필터](xref:mvc/controllers/filters#authorization-filters) 액세스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-107">The conventions described in this topic automatically apply [authorization filters](xref:mvc/controllers/filters#authorization-filters) to control access.</span></span>

<span data-ttu-id="1f263-108">[샘플 코드 보기 또는 다운로드](https://github.com/aspnet/Docs/tree/master/aspnetcore/security/authorization/razor-pages-authorization/sample)([다운로드 방법](xref:tutorials/index#how-to-download-a-sample))</span><span class="sxs-lookup"><span data-stu-id="1f263-108">[View or download sample code](https://github.com/aspnet/Docs/tree/master/aspnetcore/security/authorization/razor-pages-authorization/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample))</span></span>

## <a name="require-authorization-to-access-a-page"></a><span data-ttu-id="1f263-109">페이지에 액세스할 수 있는 인증 필요</span><span class="sxs-lookup"><span data-stu-id="1f263-109">Require authorization to access a page</span></span>

<span data-ttu-id="1f263-110">사용 하 여는 [AuthorizePage](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizepage) 규칙을 통해 [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) 추가 하는 [AuthorizeFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.authorizefilter) 지정된 된 경로에 대 한 페이지에:</span><span class="sxs-lookup"><span data-stu-id="1f263-110">Use the [AuthorizePage](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizepage) convention via [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) to add an [AuthorizeFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.authorizefilter) to the page at the specified path:</span></span>

[!code-csharp[Main](razor-pages-authorization/sample/Startup.cs?name=snippet1&highlight=2,4)]

<span data-ttu-id="1f263-111">지정한 경로가 뷰 엔진 경로 슬래시를 포함 하 고 확장명 없이 Razor 페이지 루트 상대 경로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-111">The specified path is the View Engine path, which is the Razor Pages root relative path without an extension and containing only forward slashes.</span></span>

<span data-ttu-id="1f263-112">[AuthorizePage 오버 로드](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizepage#Microsoft_Extensions_DependencyInjection_PageConventionCollectionExtensions_AuthorizePage_Microsoft_AspNetCore_Mvc_ApplicationModels_PageConventionCollection_System_String_System_String_) 권한 부여 정책을 지정 해야 할 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-112">An [AuthorizePage overload](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizepage#Microsoft_Extensions_DependencyInjection_PageConventionCollectionExtensions_AuthorizePage_Microsoft_AspNetCore_Mvc_ApplicationModels_PageConventionCollection_System_String_System_String_) is available if you need to specify an authorization policy.</span></span>

## <a name="require-authorization-to-access-a-folder-of-pages"></a><span data-ttu-id="1f263-113">페이지 폴더에 액세스할 수 있는 인증 필요</span><span class="sxs-lookup"><span data-stu-id="1f263-113">Require authorization to access a folder of pages</span></span>

<span data-ttu-id="1f263-114">사용 하 여는 [AuthorizeFolder](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizefolder) 규칙을 통해 [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) 추가 하는 [AuthorizeFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.authorizefilter) 의 모든 페이지에 지정된 된 경로에 폴더:</span><span class="sxs-lookup"><span data-stu-id="1f263-114">Use the [AuthorizeFolder](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizefolder) convention via [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) to add an [AuthorizeFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.authorizefilter) to all of the pages in a folder at the specified path:</span></span>

[!code-csharp[Main](razor-pages-authorization/sample/Startup.cs?name=snippet1&highlight=2,5)]

<span data-ttu-id="1f263-115">지정한 경로가 뷰 엔진 경로 Razor 페이지 루트의 상대 경로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-115">The specified path is the View Engine path, which is the Razor Pages root relative path.</span></span>

<span data-ttu-id="1f263-116">[AuthorizeFolder 오버 로드](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizefolder#Microsoft_Extensions_DependencyInjection_PageConventionCollectionExtensions_AuthorizeFolder_Microsoft_AspNetCore_Mvc_ApplicationModels_PageConventionCollection_System_String_System_String_) 권한 부여 정책을 지정 해야 할 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-116">An [AuthorizeFolder overload](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.authorizefolder#Microsoft_Extensions_DependencyInjection_PageConventionCollectionExtensions_AuthorizeFolder_Microsoft_AspNetCore_Mvc_ApplicationModels_PageConventionCollection_System_String_System_String_) is available if you need to specify an authorization policy.</span></span>

## <a name="allow-anonymous-access-to-a-page"></a><span data-ttu-id="1f263-117">페이지에 익명 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="1f263-117">Allow anonymous access to a page</span></span>

<span data-ttu-id="1f263-118">사용 하 여는 [AllowAnonymousToPage](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.allowanonymoustopage) 규칙을 통해 [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) 추가 하는 [AllowAnonymousFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.allowanonymousfilter) 지정된 된 경로에 페이지에:</span><span class="sxs-lookup"><span data-stu-id="1f263-118">Use the [AllowAnonymousToPage](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.allowanonymoustopage) convention via [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) to add an [AllowAnonymousFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.allowanonymousfilter) to a page at the specified path:</span></span>

[!code-csharp[Main](razor-pages-authorization/sample/Startup.cs?name=snippet1&highlight=2,6)]

<span data-ttu-id="1f263-119">지정한 경로가 뷰 엔진 경로 슬래시를 포함 하 고 확장명 없이 Razor 페이지 루트 상대 경로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-119">The specified path is the View Engine path, which is the Razor Pages root relative path without an extension and containing only forward slashes.</span></span>

## <a name="allow-anonymous-access-to-a-folder-of-pages"></a><span data-ttu-id="1f263-120">페이지의 폴더에 대 한 익명 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="1f263-120">Allow anonymous access to a folder of pages</span></span>

<span data-ttu-id="1f263-121">사용 하 여는 [AllowAnonymousToFolder](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.allowanonymoustofolder) 규칙을 통해 [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) 추가 하는 [AllowAnonymousFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.allowanonymousfilter) 의 모든 페이지에 지정된 된 경로에 폴더:</span><span class="sxs-lookup"><span data-stu-id="1f263-121">Use the [AllowAnonymousToFolder](/dotnet/api/microsoft.extensions.dependencyinjection.pageconventioncollectionextensions.allowanonymoustofolder) convention via [AddRazorPagesOptions](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.addrazorpagesoptions) to add an [AllowAnonymousFilter](/dotnet/api/microsoft.aspnetcore.mvc.authorization.allowanonymousfilter) to all of the pages in a folder at the specified path:</span></span>

[!code-csharp[Main](razor-pages-authorization/sample/Startup.cs?name=snippet1&highlight=2,7)]

<span data-ttu-id="1f263-122">지정한 경로가 뷰 엔진 경로 Razor 페이지 루트의 상대 경로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-122">The specified path is the View Engine path, which is the Razor Pages root relative path.</span></span>

## <a name="note-on-combining-authorized-and-anonymous-access"></a><span data-ttu-id="1f263-123">익명 액세스 및 권한이 결합에 대 한 참고</span><span class="sxs-lookup"><span data-stu-id="1f263-123">Note on combining authorized and anonymous access</span></span>

<span data-ttu-id="1f263-124">완벽 하 게 페이지 관련 폴더 권한을 부여 받아야 및 해당 폴더 내의 페이지 익명 액세스를 허용 하는지 지정 하는 것이 올바릅니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-124">It's perfectly valid to specify that a folder of pages require authorization and specify that a page within that folder allows anonymous access:</span></span>

```csharp
// This works.
.AuthorizeFolder("/Private").AllowAnonymousToPage("/Private/Public")
```

<span data-ttu-id="1f263-125">그러나 그 반대의 경우은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-125">The reverse, however, isn't true.</span></span> <span data-ttu-id="1f263-126">익명 액세스에 대 한 페이지의 폴더를 선언 하 고 권한 부여를 위해 내에서 페이지를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-126">You can't declare a folder of pages for anonymous access and specify a page within for authorization:</span></span>

```csharp
// This doesn't work!
.AllowAnonymousToFolder("/Public").AuthorizePage("/Public/Private") 
```

<span data-ttu-id="1f263-127">개인 페이지에 권한 부여가 필요한 수 없으므로 작동 하지 때 모두는 `AllowAnonymousFilter` 및 `AuthorizeFilter` 페이지에 필터가 적용 된는 `AllowAnonymousFilter` wins 및 액세스를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f263-127">Requiring authorization on the Private page won't work because when both the `AllowAnonymousFilter` and `AuthorizeFilter` filters are applied to the page, the `AllowAnonymousFilter` wins and controls access.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f263-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f263-128">See also</span></span>

* [<span data-ttu-id="1f263-129">Razor 페이지 사용자 지정 경로 및 페이지 모델 공급자</span><span class="sxs-lookup"><span data-stu-id="1f263-129">Razor Pages custom route and page model providers</span></span>](xref:mvc/razor-pages/razor-pages-convention-features)
* <span data-ttu-id="1f263-130">[PageConventionCollection](/dotnet/api/microsoft.aspnetcore.mvc.applicationmodels.pageconventioncollection) 클래스</span><span class="sxs-lookup"><span data-stu-id="1f263-130">[PageConventionCollection](/dotnet/api/microsoft.aspnetcore.mvc.applicationmodels.pageconventioncollection) class</span></span>