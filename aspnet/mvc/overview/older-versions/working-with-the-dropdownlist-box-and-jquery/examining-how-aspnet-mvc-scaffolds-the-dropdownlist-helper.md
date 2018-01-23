---
uid: mvc/overview/older-versions/working-with-the-dropdownlist-box-and-jquery/examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper
title: "ASP.NET MVC DropDownList 도우미 scaffolds 하는 방법을 검사 | Microsoft Docs"
author: Rick-Anderson
description: 
ms.author: aspnetcontent
manager: wpickett
ms.date: 01/12/2012
ms.topic: article
ms.assetid: 8921d7f2-21f0-427a-8b27-2df7251174b0
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions/working-with-the-dropdownlist-box-and-jquery/examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper
msc.type: authoredcontent
ms.openlocfilehash: b5210f9a29f82fbadd0e6dd2d81bd85e7f23ae7e
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2017
---
<a name="examining--how--aspnet-mvc-scaffolds-the-dropdownlist-helper"></a><span data-ttu-id="10024-102">ASP.NET MVC DropDownList 도우미 scaffolds 하는 방법을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-102">Examining  how  ASP.NET MVC scaffolds the DropDownList Helper</span></span>
====================
<span data-ttu-id="10024-103">으로 [Rick Anderson](https://github.com/Rick-Anderson)</span><span class="sxs-lookup"><span data-stu-id="10024-103">by [Rick Anderson](https://github.com/Rick-Anderson)</span></span>

<span data-ttu-id="10024-104">**솔루션 탐색기**를 마우스 오른쪽 단추로 클릭는 *컨트롤러* 폴더 및 다음 선택 **컨트롤러 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-104">In **Solution Explorer**, right-click the *Controllers* folder and then select **Add Controller**.</span></span> <span data-ttu-id="10024-105">컨트롤러 이름을 **StoreManagerController**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-105">Name the controller **StoreManagerController**.</span></span> <span data-ttu-id="10024-106">에 대 한 옵션을 설정는 **컨트롤러 추가** 아래 그림과 같이 대화 상자.</span><span class="sxs-lookup"><span data-stu-id="10024-106">Set the options for the **Add Controller** dialog as shown in the image below.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image1.png)

<span data-ttu-id="10024-107">편집 된 *StoreManager\Index.cshtml* 확인 하 여 제거 `AlbumArtUrl`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-107">Edit the *StoreManager\Index.cshtml* view and remove `AlbumArtUrl`.</span></span> <span data-ttu-id="10024-108">제거 `AlbumArtUrl` 프레젠테이션을 가독성을 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-108">Removing `AlbumArtUrl` will make the presentation more readable.</span></span> <span data-ttu-id="10024-109">완성 된 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-109">The completed code is shown below.</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample1.cshtml)]

<span data-ttu-id="10024-110">열기는 *Controllers\StoreManagerController.cs* 파일을 찾을 `Index` 메서드.</span><span class="sxs-lookup"><span data-stu-id="10024-110">Open the *Controllers\StoreManagerController.cs* file and find the `Index` method.</span></span> <span data-ttu-id="10024-111">추가 `OrderBy` 절 하므로 앨범 가격으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-111">Add the `OrderBy` clause so the albums will be sorted by price.</span></span> <span data-ttu-id="10024-112">전체 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-112">The complete code is shown below.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample2.cs)]

<span data-ttu-id="10024-113">가격으로 정렬 됩니다 간편한 방법이 데이터베이스에 변경 내용을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-113">Sorting by price will make it easier to test changes to the database.</span></span> <span data-ttu-id="10024-114">편집을 테스트 하는 메서드를 만들 때 저장된 된 데이터는 첫 번째 표시 낮은 가격을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-114">When you are testing the edit and create methods, you can use a low price so the saved data will appear first.</span></span>

<span data-ttu-id="10024-115">열기는 *StoreManager\Edit.cshtml* 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-115">Open the *StoreManager\Edit.cshtml* file.</span></span> <span data-ttu-id="10024-116">범례 태그 바로 뒤에 다음 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-116">Add the following line just after the legend tag.</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample3.cshtml)]

<span data-ttu-id="10024-117">다음 코드에서는이 변경의 컨텍스트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10024-117">The following code shows the context of this change:</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample4.cshtml)]

<span data-ttu-id="10024-118">`AlbumId` 앨범 레코드를 변경 하려면 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-118">The `AlbumId` is required to make changes to an album record.</span></span>

<span data-ttu-id="10024-119">Ctrl+F5를 눌러 응용 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-119">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="10024-120">선택는 **Admin** 링크를 선택 합니다는 **새로 만들기** 앨범을 링크 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-120">Select to the **Admin** link, then select the **Create New** link to create a new album.</span></span> <span data-ttu-id="10024-121">앨범 정보가 저장 된 것을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-121">Verify the album information was saved.</span></span> <span data-ttu-id="10024-122">앨범을 편집 하 고 변경 내용을 유지 됩니다 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-122">Edit an album and verify the changes you made are persisted.</span></span>

### <a name="the-album-schema"></a><span data-ttu-id="10024-123">앨범 스키마</span><span class="sxs-lookup"><span data-stu-id="10024-123">The Album Schema</span></span>

<span data-ttu-id="10024-124">`StoreManager` MVC 스 캐 폴딩 메커니즘으로 만들어진 컨트롤러 음악 저장소 데이터베이스에는 앨범에 대 한 CRUD (만들기, 읽기, 업데이트, 삭제) 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-124">The `StoreManager` controller created by the MVC scaffolding mechanism allows CRUD (Create, Read, Update, Delete) access to the albums in the music store database.</span></span> <span data-ttu-id="10024-125">앨범 정보에 대 한 스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-125">The schema for album information is shown below:</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image2.png)

<span data-ttu-id="10024-126">`Albums` 앨범 genre 및 설명에는 테이블에 저장 하지 않으므로, 외래 키를 저장 된 `Genres` 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-126">The `Albums` table does not store the album genre and description, it stores a foreign key to the `Genres` table.</span></span> <span data-ttu-id="10024-127">`Genres` 테이블 장르 이름 및 설명을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-127">The `Genres` table contains the genre name and description.</span></span> <span data-ttu-id="10024-128">마찬가지로,는 `Albums` 앨범 예술가 이름은 같지만 대 한 외래 키 테이블에 포함 하지 않습니다는 `Artists` 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-128">Likewise, the `Albums` table doesn't contain the album artists name, but a foreign key to the `Artists` table.</span></span> <span data-ttu-id="10024-129">`Artists` 테이블 음악가 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-129">The `Artists` table contains the artist's name.</span></span> <span data-ttu-id="10024-130">데이터를 검사 하는 경우는 `Albums` 테이블에 외래 키를 포함 하는 각 행을 볼 수 있습니다는 `Genres` 테이블과 외래 키를는 `Artists` 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-130">If you examine the data in the `Albums` table, you can see each row contains a foreign key to the `Genres` table and a foreign key to the `Artists` table.</span></span> <span data-ttu-id="10024-131">아래 이미지의 일부 테이블 데이터 표시는 `Albums` 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-131">The image below show some table data from the `Albums` table.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image3.png)

### <a name="the-html-select-tag"></a><span data-ttu-id="10024-132">HTML 선택 태그</span><span class="sxs-lookup"><span data-stu-id="10024-132">The HTML Select Tag</span></span>

<span data-ttu-id="10024-133">HTML `<select>` 요소 (HTML에서 만든 [DropDownList](https://msdn.microsoft.com/en-us/library/dd492948.aspx) 도우미) 값 (예: 장르 목록)의 전체 목록을 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-133">The HTML `<select>` element (created by the HTML [DropDownList](https://msdn.microsoft.com/en-us/library/dd492948.aspx) helper) is used to display a complete list of values (such as the list of genres).</span></span> <span data-ttu-id="10024-134">편집 폼에 대 한 select 목록의 현재 값을 확인 하면 현재 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-134">For edit forms, when the current value is known, the select list can display the current value.</span></span> <span data-ttu-id="10024-135">에 대해 살펴보았습니다이 이전에 선택한 값을 설정 했습니다 **코미디**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-135">We saw this previously when we set the selected value to **Comedy**.</span></span> <span data-ttu-id="10024-136">Select 목록 범주 또는 외래 키 데이터를 표시 하기 위해 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-136">The select list is ideal for displaying category or foreign key data.</span></span> <span data-ttu-id="10024-137">`<select>` 장르 외래 키에 대 한 요소 표시 가능한 장르 이름의 목록을 하지만 양식을 저장 된 장르 외래 키 값으로 표시 된 장르 이름이 아니라 장르 속성이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-137">The `<select>` element for the Genre foreign key displays the list of possible genre names, but when you save the form the Genre property is updated with the Genre foreign key value, not the displayed genre name.</span></span> <span data-ttu-id="10024-138">아래 그림에서는 선택한 genre가 **Disco** 음악가 이며 **Donna 여름**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-138">In the image below, the genre selected is **Disco** and the artist is **Donna Summer**.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image4.png)

### <a name="examining-the-aspnet-mvc-scaffolded-code"></a><span data-ttu-id="10024-139">코드 스 캐 폴드 된 ASP.NET MVC를 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-139">Examining the ASP.NET MVC Scaffolded Code</span></span>

<span data-ttu-id="10024-140">열기는 *Controllers\StoreManagerController.cs* 파일을 찾을 `HTTP GET Create` 메서드.</span><span class="sxs-lookup"><span data-stu-id="10024-140">Open the *Controllers\StoreManagerController.cs* file and find the `HTTP GET Create` method.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample5.cs)]

<span data-ttu-id="10024-141">`Create` 메서드 두 개를 추가 [SelectList](https://msdn.microsoft.com/en-us/library/system.web.mvc.selectlist.aspx) 개체는 `ViewBag`, 음악가 정보를 포함 하도록 여러 개 있는 장르 정보를 포함 하도록 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-141">The `Create` method adds two [SelectList](https://msdn.microsoft.com/en-us/library/system.web.mvc.selectlist.aspx) objects to the `ViewBag`, one to contain the genre information, and one to contain the artist information.</span></span> <span data-ttu-id="10024-142">[SelectList](https://msdn.microsoft.com/en-us/library/dd505286.aspx) 위에서 사용한 생성자 오버 로드는 세 개의 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-142">The [SelectList](https://msdn.microsoft.com/en-us/library/dd505286.aspx) constructor overload used above takes three arguments:</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample6.cs)]

1. <span data-ttu-id="10024-143">*항목*:는 [IEnumerable](https://msdn.microsoft.com/en-us/library/system.collections.ienumerable.aspx) 목록에 항목을 포함 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-143">*items*: An [IEnumerable](https://msdn.microsoft.com/en-us/library/system.collections.ienumerable.aspx) containing the items in the list.</span></span> <span data-ttu-id="10024-144">반환 된 장르 목록 위의 예에서 `db.Genres`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-144">In the example above, the list of genres returned by `db.Genres`.</span></span>
2. <span data-ttu-id="10024-145">*dataValueField*:에 속성의 이름은 **IEnumerable** 키 값이 포함 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-145">*dataValueField*: The name of the property in the **IEnumerable** list that contains the key value.</span></span> <span data-ttu-id="10024-146">위의 예에서 `GenreId` 및 `ArtistId`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-146">In the example above, `GenreId` and `ArtistId`.</span></span>
3. <span data-ttu-id="10024-147">*dataTextField*:에 속성의 이름은 **IEnumerable** 표시할 정보를 포함 하는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-147">*dataTextField*: The name of the property in the **IEnumerable** list that contains the information to display.</span></span> <span data-ttu-id="10024-148">예술가 장르 테이블에는 `name` 필드가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-148">In both the artists and genre table, the `name` field is used.</span></span>

<span data-ttu-id="10024-149">열기는 *Views\StoreManager\Create.cshtml* 파일 및 검사는 `Html.DropDownList` genre 필드에 대 한 도우미 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-149">Open the *Views\StoreManager\Create.cshtml* file and examine the `Html.DropDownList` helper markup for the genre field.</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample7.cshtml)]

<span data-ttu-id="10024-150">첫 번째 줄 만들기 뷰를 사용 한다고 표시는 `Album` 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-150">The first line shows that the create view takes an `Album` model.</span></span> <span data-ttu-id="10024-151">에 `Create` 위에 표시 된 모델이 전달 된 보기 가져옵니다 하므로 메서드는 **null** `Album` 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-151">In the `Create` method shown above, no model was passed, so the view gets a **null** `Album` model.</span></span> <span data-ttu-id="10024-152">이 시점에서 만드므로 새 앨범 모든 사항이 `Album` 것에 대 한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-152">At this point we are creating a new album so we don't have any `Album` data for it.</span></span>

<span data-ttu-id="10024-153">[Html.DropDownList](https://msdn.microsoft.com/en-us/library/dd492948.aspx) 위에 표시 된 오버 로드를 모델 바인딩할 필드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-153">The [Html.DropDownList](https://msdn.microsoft.com/en-us/library/dd492948.aspx) overload shown above takes the name of the field to bind to the model.</span></span> <span data-ttu-id="10024-154">또한 사용 하 여이 이름을 찾습니다는 **ViewBag** 포함 된 개체는 [SelectList](https://msdn.microsoft.com/en-us/library/dd505286.aspx) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-154">It also uses this name to look for a **ViewBag** object containing a [SelectList](https://msdn.microsoft.com/en-us/library/dd505286.aspx) object.</span></span> <span data-ttu-id="10024-155">이 오버 로드를 사용 해야 하는 이름을 **ViewBag SelectList** 개체 `GenreId`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-155">Using this overload, you are required to name the **ViewBag SelectList** object `GenreId`.</span></span> <span data-ttu-id="10024-156">두 번째 매개 변수 (`String.Empty`)은 선택 된 항목이 때 표시할 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-156">The second parameter (`String.Empty`) is the text to display when no item is selected.</span></span> <span data-ttu-id="10024-157">이 새 앨범을 만들 때 원하는 대로 정확 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-157">This is exactly what we want when creating a new album.</span></span> <span data-ttu-id="10024-158">두 번째 매개 변수를 제거 하 고 다음 코드를 사용:</span><span class="sxs-lookup"><span data-stu-id="10024-158">If you removed the second parameter and used the following code:</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample8.cshtml)]

<span data-ttu-id="10024-159">Select 목록이 샘플의 기본적으로 첫 번째 요소 또는 록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-159">The select list would default to the first element, or Rock in our sample.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image5.png)

<span data-ttu-id="10024-160">검사 하 여 `HTTP POST Create` 메서드.</span><span class="sxs-lookup"><span data-stu-id="10024-160">Examining the `HTTP POST Create` method.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample9.cs)]

<span data-ttu-id="10024-161">이 오버 로드는 `Create` 메서드는 `album` 게시 된 양식 값에서 ASP.NET MVC 모델 바인딩 시스템이 생성 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-161">This overload of the `Create` method takes an `album` object, created by the ASP.NET MVC model binding system from the form values posted.</span></span> <span data-ttu-id="10024-162">모델 상태가 유효 하 고 데이터베이스 오류가 없는 경우 새 앨범을 제출 하면 새 앨범이 데이터베이스를 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-162">When you submit a new album, if model state is valid and there are no database errors, the new album is added the database.</span></span> <span data-ttu-id="10024-163">다음 이미지는 새 앨범 만드는 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10024-163">The following image shows the creation of a new album.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image6.png)

<span data-ttu-id="10024-164">사용할 수는 [fiddler 도구](http://www.fiddler2.com/fiddler2/) 게시 된 양식 값을 검사 하려면 해당 ASP.NET MVC 모델 바인딩 앨범 개체를 만드는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-164">You can use the [fiddler tool](http://www.fiddler2.com/fiddler2/) to examine the posted form values that ASP.NET MVC model binding uses to create the album object.</span></span>

<span data-ttu-id="10024-165">![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image7.png).</span><span class="sxs-lookup"><span data-stu-id="10024-165">![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image7.png).</span></span>

### <a name="refactoring-the-viewbag-selectlist-creation"></a><span data-ttu-id="10024-166">ViewBag SelectList 만들기 리팩터링</span><span class="sxs-lookup"><span data-stu-id="10024-166">Refactoring the ViewBag SelectList Creation</span></span>

<span data-ttu-id="10024-167">두는 `Edit` 메서드 및 `HTTP POST Create` 메서드는 동일한 코드를 설정 하는 **SelectList** 에 **ViewBag**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-167">Both the `Edit` methods and the `HTTP POST Create` method have identical code to set up the **SelectList** in the **ViewBag**.</span></span> <span data-ttu-id="10024-168">목적에 [건조](http://en.wikipedia.org/wiki/Don't_repeat_yourself),이 코드를 리팩터링한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-168">In the spirit of [DRY](http://en.wikipedia.org/wiki/Don't_repeat_yourself), we will refactor this code.</span></span> <span data-ttu-id="10024-169">만들면이 사용 하 여 나중에 코드를 리팩터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-169">We'll make use of this refactored code later.</span></span>

<span data-ttu-id="10024-170">Genre 및 아티스트를 추가 하려면 새 메서드를 만들 **SelectList** 에 **ViewBag**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-170">Create a new method to add a genre and artist **SelectList** to the **ViewBag**.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample10.cs)]

<span data-ttu-id="10024-171">설정 두 줄을 바꿀는 `ViewBag` 각는 `Create` 및 `Edit` 메서드를 호출 하 여는 `SetGenreArtistViewBag` 메서드.</span><span class="sxs-lookup"><span data-stu-id="10024-171">Replace the two lines setting the `ViewBag` in each of the `Create` and `Edit` methods with a call to the `SetGenreArtistViewBag` method.</span></span> <span data-ttu-id="10024-172">완성 된 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-172">The completed code is shown below.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample11.cs)]

<span data-ttu-id="10024-173">새 앨범이 만들고 작동 하는 변경 내용을 확인 하기 위해 앨범을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-173">Create a new album and edit an album to verify the changes work.</span></span>

### <a name="explicitly-passing-the-selectlist-to-the-dropdownlist"></a><span data-ttu-id="10024-174">드롭다운 목록에는 SelectList를 명시적으로 전달</span><span class="sxs-lookup"><span data-stu-id="10024-174">Explicitly Passing the SelectList to the DropDownList</span></span>

<span data-ttu-id="10024-175">ASP.NET MVC 스 캐 폴딩 사용 하 여 만든 만들기 및 편집 뷰 다음 **DropDownList** 오버 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-175">The create and edit views created by the ASP.NET MVC scaffolding use the following **DropDownList** overload:</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample12.cs)]

<span data-ttu-id="10024-176">`DropDownList` 뷰 만들기에 대 한 태그는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-176">The `DropDownList` markup for the create view is shown below.</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample13.cshtml)]

<span data-ttu-id="10024-177">때문에 `ViewBag` 속성에 대 한는 `SelectList` 라는 `GenreId`, **DropDownList** 도우미 ´ ֲ는 `GenreId` **SelectList** 에 **ViewBag** .</span><span class="sxs-lookup"><span data-stu-id="10024-177">Because the `ViewBag` property for the `SelectList` is named `GenreId`, the **DropDownList** helper will use the `GenreId`**SelectList** in the **ViewBag**.</span></span> <span data-ttu-id="10024-178">다음에서 **DropDownList** 오버 로드는 `SelectList` 에 명시적으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-178">In the following **DropDownList** overload, the `SelectList` is explicitly passed in.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample14.cs)]

<span data-ttu-id="10024-179">열기는 *Views\StoreManager\Edit.cshtml* 파일을 찾아 변경는 **DropDownList** 호출에서 명시적으로 전달 하도록는 **SelectList**, 위의 오버 로드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-179">Open the *Views\StoreManager\Edit.cshtml* file, and change the **DropDownList** call to explicitly pass in the **SelectList**, using the overload above.</span></span> <span data-ttu-id="10024-180">Genre 범주에 대 한이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-180">Do this for the Genre category.</span></span> <span data-ttu-id="10024-181">완성 된 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-181">The completed code is shown below:</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample15.cshtml)]

<span data-ttu-id="10024-182">응용 프로그램을 실행 하 고 클릭는 **관리자** 링크를 다음 Jazz 앨범으로 이동한 후 선택 된 **편집** 링크 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-182">Run the application and click the **Admin** link, then navigate to a Jazz album and select the **Edit** link.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image8.png)

<span data-ttu-id="10024-183">현재 선택 된 장르로 Jazz 숨겨지므로 록 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-183">Instead of showing Jazz as the currently selected genre, Rock is displayed.</span></span> <span data-ttu-id="10024-184">때 문자열 인수 (바인딩할 속성) 및 **SelectList** 개체 이름이 같은, 선택한 값은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-184">When the string argument (the property to bind) and the **SelectList** object have the same name, the selected value is not used.</span></span> <span data-ttu-id="10024-185">브라우저의 첫 번째 요소에 기본 제공 된 선택한 값 없음 이면는 **SelectList**(변수인 **록** 위의 예제에서).</span><span class="sxs-lookup"><span data-stu-id="10024-185">When there is no selected value provided, browsers default to the first element in the **SelectList**(which is **Rock** in the example above).</span></span> <span data-ttu-id="10024-186">이것은 알려진된 제한인은 **DropDownList** 도우미입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-186">This is a known limitation of the **DropDownList** helper.</span></span>

<span data-ttu-id="10024-187">열기는 *Controllers\StoreManagerController.cs* 파일 및 변경의 **SelectList** 개체 이름에 `Genres` 및 `Artists`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-187">Open the *Controllers\StoreManagerController.cs* file and change the **SelectList** object names to `Genres` and `Artists`.</span></span> <span data-ttu-id="10024-188">완성 된 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-188">The completed code is shown below:</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample16.cs)]

<span data-ttu-id="10024-189">장르와 예술가 이름을 각 범주의 ID 보다 더을 포함 하는 범주에 대 한 더 나은 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-189">The names Genres and Artists are better names for the categories, as they contain more than just the ID of each category.</span></span> <span data-ttu-id="10024-190">이전에 수행한 리팩터링 지불 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-190">The refactoring we did earlier paid off.</span></span> <span data-ttu-id="10024-191">변경 하는 대신는 **ViewBag** 네 가지 메서드가 우리의 변경 내용이 격리 하는 `SetGenreArtistViewBag` 메서드.</span><span class="sxs-lookup"><span data-stu-id="10024-191">Instead of changing the **ViewBag** in four methods, our changes were isolated to the `SetGenreArtistViewBag` method.</span></span>

<span data-ttu-id="10024-192">변경 된 **DropDownList** 만들기에서 호출 하 고는 new를 사용 하는 보기를 편집할 **SelectList** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-192">Change the **DropDownList** call in the create and edit views to use the new **SelectList** names.</span></span> <span data-ttu-id="10024-193">편집 보기에 대 한 새 태그는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-193">The new markup for the edit view is shown below:</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample17.cshtml)]

<span data-ttu-id="10024-194">Create view는 SelectList 첫 번째 항목 표시 되지 않도록 방지 하는 빈 문자열을 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-194">The Create view requires an empty string to prevent the first item in the SelectList from being displayed.</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample18.cshtml)]

<span data-ttu-id="10024-195">새 앨범이 만들고 작동 하는 변경 내용을 확인 하기 위해 앨범을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-195">Create a new album and edit an album to verify the changes work.</span></span> <span data-ttu-id="10024-196">코드 편집 록 이외의 장르와 앨범을 선택 하 여 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-196">Test the edit code by selecting an album with a genre other than Rock.</span></span>

### <a name="using-a-view-model-with-the-dropdownlist-helper"></a><span data-ttu-id="10024-197">뷰 모델을 사용 하 여 DropDownList 도우미 사용</span><span class="sxs-lookup"><span data-stu-id="10024-197">Using a View Model with the DropDownList Helper</span></span>

<span data-ttu-id="10024-198">명명 된 Viewmodel 폴더에서 새 클래스 만들기 `AlbumSelectListViewModel`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-198">Create a new class in the ViewModels folder named `AlbumSelectListViewModel`.</span></span> <span data-ttu-id="10024-199">코드는 `AlbumSelectListViewModel` 다음을 사용 하 여 클래스:</span><span class="sxs-lookup"><span data-stu-id="10024-199">Replace the code in the `AlbumSelectListViewModel` class with the following:</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample19.cs)]

<span data-ttu-id="10024-200">`AlbumSelectListViewModel` 생성자 앨범, 아티스트, 장르 목록 고 앨범을 포함 하는 개체를 만들고 및 `SelectList` 장르와 예술가 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-200">The `AlbumSelectListViewModel` constructor takes an album, a list of artists and genres and creates an object containing the album and a `SelectList` for genres and artists.</span></span>

<span data-ttu-id="10024-201">프로젝트 빌드 하므로 `AlbumSelectListViewModel` 를 다음 단계에서 뷰를 만들 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-201">Build the project so the `AlbumSelectListViewModel` is available when we create a view in the next step.</span></span>

<span data-ttu-id="10024-202">추가 `EditVM` 메서드는 `StoreManagerController`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-202">Add an `EditVM` method to the `StoreManagerController`.</span></span> <span data-ttu-id="10024-203">완성 된 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-203">The completed code is shown below.</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample20.cs)]

<span data-ttu-id="10024-204">마우스 오른쪽 단추로 클릭 `AlbumSelectListViewModel`선택, **해결**, 다음 **MvcMusicStore.ViewModels;를 사용 하 여**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-204">Right click `AlbumSelectListViewModel`, select **Resolve**, then **using MvcMusicStore.ViewModels;**.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image9.png)

<span data-ttu-id="10024-205">또는 다음을 추가할 수 문을 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="10024-205">Alternatively, you can add the following using statement:</span></span>

[!code-csharp[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample21.cs)]

<span data-ttu-id="10024-206">마우스 오른쪽 단추로 클릭 `EditVM` 선택 **뷰 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-206">Right click `EditVM` and select **Add View**.</span></span> <span data-ttu-id="10024-207">아래 표시 된 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-207">Use the options shown below.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image10.png)

<span data-ttu-id="10024-208">선택 **추가**, 다음의 내용을 바꿉니다는 *Views\StoreManager\EditVM.cshtml* 다음 파일:</span><span class="sxs-lookup"><span data-stu-id="10024-208">Select **Add**, then replace the contents of the *Views\StoreManager\EditVM.cshtml* file with the following:</span></span>

[!code-cshtml[Main](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/samples/sample22.cshtml)]

<span data-ttu-id="10024-209">`EditVM` 태그는 원래와 매우 유사 `Edit` 태그는 다음과 같은 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-209">The `EditVM` markup is very similar to the original `Edit` markup with the following exceptions.</span></span>

- <span data-ttu-id="10024-210">모델 속성에는 `Edit` 보기는 `model.property`(예를 들어 `model.Title` ).</span><span class="sxs-lookup"><span data-stu-id="10024-210">Model properties in the `Edit` view are of the form `model.property`(for example, `model.Title` ).</span></span> <span data-ttu-id="10024-211">모델 속성에는 `EditVm` 보기는 `model.Album.property`(예를 들어 `model.Album.Title`).</span><span class="sxs-lookup"><span data-stu-id="10024-211">Model properties in the `EditVm` view are of the form `model.Album.property`(for example, `model.Album.Title`).</span></span> <span data-ttu-id="10024-212">때문는 `EditVM` 보기에 대 한 컨테이너를 전달 되는 `Album`이 아니라는 `Album` 에서 같이 `Edit` 보기.</span><span class="sxs-lookup"><span data-stu-id="10024-212">That's because the `EditVM` view is passed a container for an `Album`, not an `Album` as in the `Edit` view.</span></span>
- <span data-ttu-id="10024-213">**DropDownList** 하지 뷰 모델에서 가져온 두 번째 매개 변수는 **ViewBag**합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-213">The **DropDownList** second parameter comes from the view model, not the **ViewBag**.</span></span>
- <span data-ttu-id="10024-214">**BeginForm** 도우미에는 `EditVM` 보기에 다시 명시적으로 게시는 `Edit` 동작 메서드.</span><span class="sxs-lookup"><span data-stu-id="10024-214">The **BeginForm** helper in the `EditVM` view explicitly posts back to the `Edit` action method.</span></span> <span data-ttu-id="10024-215">에 다시 게시 하 여는 `Edit` 동작을 않아도 작성 하는 `HTTP POST EditVM` 동작 다시 사용할 수 있습니다는 `HTTP POST` `Edit` 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-215">By posting back to the `Edit` action, we don't have to write an `HTTP POST EditVM` action and can reuse the `HTTP POST` `Edit` action.</span></span>

<span data-ttu-id="10024-216">응용 프로그램을 실행 하 고 앨범을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-216">Run the application and edit an album.</span></span> <span data-ttu-id="10024-217">URL이 사용 하도록 변경 `EditVM`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-217">Change the URL to use `EditVM`.</span></span> <span data-ttu-id="10024-218">필드를 변경 하 고 적중는 **저장** 코드가 작동 중인지 확인 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-218">Change a field and hit the **Save** button to verify the code is working.</span></span>

![](examining-how-aspnet-mvc-scaffolds-the-dropdownlist-helper/_static/image11.png)

### <a name="which-approach-should-you-use"></a><span data-ttu-id="10024-219">어떤 방법이 언제 사용 하나요?</span><span class="sxs-lookup"><span data-stu-id="10024-219">Which Approach Should You Use?</span></span>

<span data-ttu-id="10024-220">표시 된 세 방법 모두 acceptible 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10024-220">All three approaches shown are acceptible.</span></span> <span data-ttu-id="10024-221">Explictily 패스에는 개발자가 많습니다는 `SelectList` 에 `DropDownList` 를 사용 하는 `ViewBag`합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-221">Many developers prefer to explictily pass the `SelectList` to the `DropDownList` using the `ViewBag`.</span></span> <span data-ttu-id="10024-222">이 방법에 컬렉션에 대 한 보다 적절 한 이름을 사용 하 여의 유연성을 제공 하는 추가 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-222">This approach has the added advantage of giving you the flexibility of using a more appropriate name for the collection.</span></span> <span data-ttu-id="10024-223">한 가지 주의할 점은 이름을 지정할 수 없습니다는 `ViewBag SelectList` 모델 속성 이름이 같은 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="10024-223">The one caveat is you cannot name the `ViewBag SelectList` object the same name as the model property.</span></span>

<span data-ttu-id="10024-224">ViewModel 접근 방식을 선호 하는 개발자도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10024-224">Some developers prefer the ViewModel approach.</span></span> <span data-ttu-id="10024-225">다른 고려 더 자세한 정보 표시 태그 및 생성 된 HTML ViewModel의 단점은 접근 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-225">Others consider the the more verbose markup and generated HTML of the ViewModel approach a disadvantage.</span></span>

<span data-ttu-id="10024-226">이 섹션에는 이전에 배운 것 세 가지 방법을 사용 하는 **DropDownList** 범주 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10024-226">In this section we have learned three approaches to using the **DropDownList** with category data.</span></span> <span data-ttu-id="10024-227">다음 섹션에서는 새 범주를 추가 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="10024-227">In the next section, we'll show how to add a new category.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="10024-228">[이전](using-the-dropdownlist-helper-with-aspnet-mvc.md)
[다음](adding-a-new-category-to-the-dropdownlist-using-jquery-ui.md)</span><span class="sxs-lookup"><span data-stu-id="10024-228">[Previous](using-the-dropdownlist-helper-with-aspnet-mvc.md)
[Next](adding-a-new-category-to-the-dropdownlist-using-jquery-ui.md)</span></span>