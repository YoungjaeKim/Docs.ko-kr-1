---
title: ASP.NET Core 프로젝트에 스 캐 폴드 Id
author: rick-anderson
description: Identity ASP.NET Core 프로젝트에 스 캐 폴딩 하는 방법에 알아봅니다.
manager: wpickett
monikerRange: '>= aspnetcore-2.1'
ms.author: riande
ms.date: 5/16/2018
ms.prod: asp.net-core
ms.technology: aspnet
ms.topic: article
uid: security/authentication/scaffold-identity
ms.openlocfilehash: 80cd39af61e856d3ce92db1c26e70788bcdca83d
ms.sourcegitcommit: 9a35906446af7ffd4ccfc18daec38874b5abbef7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35725821"
---
# <a name="scaffold-identity-in-aspnet-core-projects"></a>ASP.NET Core 프로젝트에 스 캐 폴드 Id

작성자: [Rick Anderson](https://twitter.com/RickAndMSFT)

ASP.NET Core 2.1 이상 제공 [ASP.NET Core Id](xref:security/authentication/identity) 로 [Razor 클래스 라이브러리](xref:mvc/razor-pages/ui-class)합니다. Id가 포함 하는 응용 프로그램에 선택적으로 Identity Razor 클래스 라이브러리 (RCL)에 포함 된 소스 코드를 추가 하려면 scaffolder를 적용할 수 있습니다. 코드를 수정 하 고 동작을 변경할 수 있도록 소스 코드를 생성 수 있습니다. 예를 들어 scaffolder 등록에 사용 하 여 코드를 생성 하도록 지정할 수 있습니다. 생성 된 코드 Identity RCL에서 동일한 코드 보다 우선합니다. UI의 모든 권한을 얻으려고 하 RCL 기본값을 사용 하지 섹션을 참조 [만들기 전체 id UI 소스](#full)합니다.

응용 프로그램을 **하지** 포함 인증 RCL Identity 패키지를 추가 하려면 scaffolder 적용할 수 있습니다. 선택 하는 옵션이 Identity 코드를 생성 해야 합니다.

scaffolder 대부분의 필요한 코드를 생성 하지만 프로세스를 완료 하려면 프로젝트를 업데이트 해야 합니다. 이 문서는 Identity 스 캐 폴딩 업데이트를 완료 하는 데 필요한 단계에 설명 합니다.

Identity scaffolder 실행 되는 *ScaffoldingReadme.txt* 파일은 프로젝트 디렉터리에 만들어집니다. *ScaffoldingReadme.txt* 파일 Identity 스 캐 폴딩 업데이트를 완료 하는 데 필요한 항목에 대 한 일반적인 지침을 포함 합니다. 이 문서에는 보다 자세한 설명은 *ScaffoldingReadme.txt* 파일입니다.

파일 차이 보여 주는 변경 취소를 사용 하면 소스 제어 시스템을 사용 하는 것이 좋습니다. Identity scaffolder 실행 한 후 변경 내용을 검사 합니다.

## <a name="scaffold-identity-into-an-empty-project"></a>빈 프로젝트에 스 캐 폴드 identity

[!INCLUDE[](~/includes/scaffold-identity/id-scaffold-dlg.md)]

강조 표시 된 다음 호출을 추가 `Startup` 클래스:

[!code-csharp[Main](scaffold-identity/sample/StartupEmpty.cs?name=snippet1&highlight=5,20-23)]

[!INCLUDE[](~/includes/scaffold-identity/hsts.md)]

[!INCLUDE[](~/includes/scaffold-identity/migrations.md)]

## <a name="scaffold-identity-into-a-razor-project-without-existing-authorization"></a>기존 인증 없이 Razor 프로젝트에 스 캐 폴드 identity

<!--
set projNam=RPnoAuth
set projType=razor
set version=2.1.0

dotnet new %projType% -o %projNam%
cd %projNam%
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design -v %version%
dotnet restore
dotnet aspnet-codegenerator identity --useDefaultUI
dotnet ef migrations add CreateIdentitySchema
dotnet ef database update
-->

[!INCLUDE[](~/includes/scaffold-identity/id-scaffold-dlg.md)]

id가 구성 *Areas/Identity/IdentityHostingStartup.cs*합니다. 자세한 내용은 참조 [IHostingStartup](xref:fundamentals/configuration/platform-specific-configuration)합니다.

<a name="efm"></a>

### <a name="migrations-useauthentication-and-layout"></a>마이그레이션, UseAuthentication, 및 레이아웃

[!INCLUDE[](~/includes/scaffold-identity/migrations.md)]

에 `Configure` 의 메서드는 `Startup` 클래스, 호출 [UseAuthentication](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.builder.authappbuilderextensions.useauthentication?view=aspnetcore-2.0#Microsoft_AspNetCore_Builder_AuthAppBuilderExtensions_UseAuthentication_Microsoft_AspNetCore_Builder_IApplicationBuilder_) 후 `UseStaticFiles`:

[!code-csharp[Main](scaffold-identity/sample/StartupRPnoAuth.cs?name=snippet1&highlight=29)]

[!INCLUDE[](~/includes/scaffold-identity/hsts.md)]

### <a name="layout-changes"></a>레이아웃 변경

선택 사항: 부분 로그인을 추가 (`_LoginPartial`) 레이아웃 파일에:

[!code-html[Main](scaffold-identity/sample/_Layout.cshtml?highlight=37)]

## <a name="scaffold-identity-into-a-razor-project-with-authorization"></a>권한 부여를 사용 하 여 Razor 프로젝트에 스 캐 폴드 identity

<!--
Use >=2.1: dotnet new webapp -au Individual -o RPauth
Use = 2.0: dotnet new razor -au Individual -o RPauth
cd RPauth
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet restore
dotnet aspnet-codegenerator identity -dc RPauth.Data.ApplicationDbContext --files Account.Register

[!INCLUDE[](~/includes/webapp-alias-notice.md)]
-->

[!INCLUDE[](~/includes/scaffold-identity/id-scaffold-dlg-auth.md)]
일부 Id 옵션에 구성 된 *Areas/Identity/IdentityHostingStartup.cs*합니다. 자세한 내용은 참조 [IHostingStartup](xref:fundamentals/configuration/platform-specific-configuration)합니다.

## <a name="scaffold-identity-into-an-mvc-project-without-existing-authorization"></a>기존 인증 없이 MVC 프로젝트에 스 캐 폴드 identity

<!--
set projNam=MvcNoAuth
set projType=mvc
set version=2.1.0

dotnet new %projType% -o %projNam%
cd %projNam%
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design -v %version%
dotnet restore
dotnet aspnet-codegenerator identity --useDefaultUI
dotnet ef migrations add CreateIdentitySchema
dotnet ef database update
-->

[!INCLUDE[](~/includes/scaffold-identity/id-scaffold-dlg.md)]

선택 사항: 부분 로그인을 추가 (`_LoginPartial`)에 *Views/Shared/_Layout.cshtml* 파일:

[!code-html[Main](scaffold-identity/sample/_LayoutMvc.cshtml?highlight=37)]

* 이동 된 *Pages/Shared/_LoginPartial.cshtml* 파일을 *Views/Shared/_LoginPartial.cshtml*

id가 구성 *Areas/Identity/IdentityHostingStartup.cs*합니다. 자세한 내용은 IHostingStartup를 참조 하십시오.

[!INCLUDE[](~/includes/scaffold-identity/migrations.md)]

호출 [UseAuthentication](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.builder.authappbuilderextensions.useauthentication?view=aspnetcore-2.0#Microsoft_AspNetCore_Builder_AuthAppBuilderExtensions_UseAuthentication_Microsoft_AspNetCore_Builder_IApplicationBuilder_) 후 `UseStaticFiles`:

[!code-csharp[Main](scaffold-identity/sample/StartupMvcNoAuth.cs?name=snippet1&highlight=23)]

[!INCLUDE[](~/includes/scaffold-identity/hsts.md)]

## <a name="scaffold-identity-into-an-mvc-project-with-authorization"></a>권한 부여를 사용 하는 MVC 프로젝트에 스 캐 폴드 identity

<!--
dotnet new mvc -au Individual -o MvcAuth
cd MvcAuth
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet restore
dotnet aspnet-codegenerator identity -dc MvcAuth.Data.ApplicationDbContext --files Account.Register
-->

[!INCLUDE[](~/includes/scaffold-identity/id-scaffold-dlg-auth.md)]

삭제 된 *페이지/공유* 폴더와 해당 폴더의 파일입니다.

<a name="full"></a>

## <a name="create-full-identity-ui-source"></a>전체 id UI 원본 만들기

Identity UI에 대 한 모든 제어를 유지 하려면 Identity scaffolder를 실행 하 고 선택 **모든 파일을 재정의**합니다.

다음 강조 표시 된 코드에는 ASP.NET Core 2.1 웹 응용 프로그램의 Id를 가진 기본 Identity UI를 바꾸려면 변경을 보여 줍니다. Identity UI의 모든 권한을 가질 수 이렇게 할 수 있습니다.

[!code-csharp[Main](scaffold-identity/sample/StartupFull.cs?name=snippet1&highlight=13-14,17-999)]

다음 코드에서 Identity 기본 대체 됩니다. [!code-csharp[Main](scaffold-identity/sample/StartupFull.cs?name=snippet2)]

다음 코드는 권한 부여를 요구 하는 Identity 페이지 권한을 부여 하는 ASP.NET Core를 구성 합니다. [!code-csharp[Main](scaffold-identity/sample/StartupFull.cs?name=snippet3)]

다음 코드에서는 올바른 Identity 페이지 경로 사용 하도록 Id 쿠키를 설정 합니다.
[!code-csharp[Main](scaffold-identity/sample/StartupFull.cs?name=snippet3)]

등록 된 `IEmailSender` 구현 예:

[!code-csharp[Main](scaffold-identity/sample/StartupFull.cs?name=snippet4)]