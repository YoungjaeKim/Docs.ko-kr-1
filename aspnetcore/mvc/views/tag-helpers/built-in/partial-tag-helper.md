﻿---
title: ASP.NET Core의 부분 태그 도우미
author: scottaddie
description: ASP.NET Core의 부분 태그 도우미와 각 특성이 부분 뷰를 렌더링할 때 수행하는 역할을 알아봅니다.
manager: wpickett
monikerRange: '>= aspnetcore-2.1'
ms.author: scaddie
ms.custom: mvc
ms.date: 04/13/2018
ms.prod: aspnet-core
ms.technology: aspnet
ms.topic: article
uid: mvc/views/tag-helpers/builtin-th/partial-tag-helper
ms.openlocfilehash: 786c333980db89a9a5a60dc70c0bd1998ca159cd
ms.sourcegitcommit: 74be78285ea88772e7dad112f80146b6ed00e53e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33962596"
---
# <a name="partial-tag-helper-in-aspnet-core"></a>ASP.NET Core의 부분 태그 도우미

작성자: [Scott Addie](https://github.com/scottaddie)

[예제 코드 살펴보기 및 다운로드](https://github.com/aspnet/Docs/tree/master/aspnetcore/mvc/views/tag-helpers/built-in/samples) ([다운로드 방법](xref:tutorials/index#how-to-download-a-sample))

## <a name="overview"></a>개요

부분 태그 도우미는 Razor 페이지 및 MVC 앱에서 [부분 뷰](xref:mvc/views/partial)를 렌더링하는 데 사용됩니다. 부분 태그 도우미는:

* ASP.NET Core 2.1 이상이 필요합니다.
* [HTML 도우미 구문](xref:mvc/views/partial#referencing-a-partial-view) 대신 사용할 수 있습니다.
* 부분 뷰를 비동기적으로 렌더링합니다.

부분 뷰를 렌더링하기 위한 HTML 도우미의 옵션은 다음과 같습니다.

* [@await Html.PartialAsync](/dotnet/api/microsoft.aspnetcore.mvc.rendering.htmlhelperpartialextensions.partialasync)
* [@await Html.RenderPartialAsync](/dotnet/api/microsoft.aspnetcore.mvc.rendering.htmlhelperpartialextensions.renderpartialasync)
* [@Html.Partial](/dotnet/api/microsoft.aspnetcore.mvc.rendering.htmlhelperpartialextensions.partial)
* [@Html.RenderPartial](/dotnet/api/microsoft.aspnetcore.mvc.rendering.htmlhelperpartialextensions.renderpartial)

이 문서의 예제 전반에서는 *Product* 모델이 사용됩니다.

[!code-csharp[](samples/TagHelpersBuiltIn/Models/Product.cs)]

부분 태그 도우미의 특성 목록은 다음과 같습니다.

## <a name="name"></a>name

`name` 특성은 필수입니다. 이 특성은 렌더링할 부분 뷰의 이름 또는 경로를 나타냅니다. 부분 뷰의 이름을 지정할 경우 [뷰 탐색](xref:mvc/views/overview#view-discovery) 과정이 시작됩니다. 명시적인 경로가 지정될 경우에는 이 과정이 생략됩니다.

다음 태그는 명시적인 경로를 사용해서 *Shared* 폴더의 *_ProductPartial.cshtml*을 로드하도록 지시합니다. [for](#for) 특성을 사용하면 바인딩을 위한 모델이 부분 뷰에 전달됩니다.

[!code-cshtml[](samples/TagHelpersBuiltIn/Pages/Product.cshtml?name=snippet_Name)]

## <a name="for"></a>for

`for` 특성은 현재 모델과 비교 평가할 [ModelExpression](/dotnet/api/microsoft.aspnetcore.mvc.viewfeatures.modelexpression)을 할당합니다. `ModelExpression`은 `@Model.` 구문을 추론합니다. 예를 들어 `for="@Model.Product"` 대신 `for="Product"`를 사용할 수 있습니다. 이 기본 추론 동작은 인라인 식을 정의하는 `@` 기호를 사용하여 재정의됩니다. `for` 특성은 [model](#model) 특성과 함께 사용할 수 없습니다.

다음 태그는 *_ProductPartial.cshtml*을 로드합니다.

[!code-cshtml[](samples/TagHelpersBuiltIn/Pages/Product.cshtml?name=snippet_For)]

부분 뷰는 연결된 페이지 모델의 `Product` 속성과 바인딩됩니다.

[!code-csharp[](samples/TagHelpersBuiltIn/Pages/Product.cshtml.cs?highlight=8)]

## <a name="model"></a>model

`model` 특성은 부분 뷰에 전달할 모델의 인스턴스를 할당합니다. `model` 특성은 [for](#for) 특성과 함께 사용할 수 없습니다.

다음 태그에서는 새로운 `Product` 개체의 인스턴스가 생성되어 바인딩을 위해 `model` 특성에 전달됩니다.

[!code-cshtml[](samples/TagHelpersBuiltIn/Pages/Product.cshtml?name=snippet_Model)]

## <a name="view-data"></a>view-data

`view-data` 특성은 부분 보기에 전달할 [ViewDataDictionary](/dotnet/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary)를 할당합니다. 다음 태그를 사용하면 부분 뷰에서 전체 ViewData 컬렉션에 접근할 수 있습니다.

[!code-cshtml[](samples/TagHelpersBuiltIn/Pages/Product.cshtml?name=snippet_ViewData&highlight=5-)]

위의 코드에서 `IsNumberReadOnly` 키 값은 `true`로 설정되고 ViewData 컬렉션에 추가됩니다. 따라서 다음 부분 뷰 내에서 `ViewData["IsNumberReadOnly"]`에 접근할 수 있습니다.

[!code-cshtml[](samples/TagHelpersBuiltIn/Pages/Shared/_ProductViewDataPartial.cshtml?highlight=5)]

이 예제에서 `ViewData["IsNumberReadOnly"]` 값은 *Number* 필드가 읽기 전용으로 표시될지 여부를 결정합니다.

## <a name="additional-resources"></a>추가 자료

* [부분 뷰](xref:mvc/views/partial)
* [약한 형식의 데이터 (ViewData, ViewData 특성 및 ViewBag)](xref:mvc/views/overview#weakly-typed-data-viewdata-viewdata-attribute-and-viewbag)