---
uid: mvc/overview/older-versions-1/contact-manager/iteration-2-make-the-application-look-nice-cs
title: "반복 #2-확인는 응용 프로그램의 모양을 좋은 (C#) | Microsoft Docs"
author: microsoft
description: "이 반복에서 기본 ASP.NET MVC 뷰 마스터 페이지를 수정 및 스타일 시트를 연계 하 여 응용 프로그램의 모양을 개선 합니다."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/20/2009
ms.topic: article
ms.assetid: f1173feb-11ee-4017-8f3f-86599ea6ae13
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions-1/contact-manager/iteration-2-make-the-application-look-nice-cs
msc.type: authoredcontent
ms.openlocfilehash: 10379f5321773155aaff4c384d8e0716d7e0e874
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2017
---
<a name="iteration-2--make-the-application-look-nice-c"></a><span data-ttu-id="f1abe-103">반복 #2-확인는 응용 프로그램의 모양을 좋은 (C#)</span><span class="sxs-lookup"><span data-stu-id="f1abe-103">Iteration #2 – Make the application look nice (C#)</span></span>
====================
<span data-ttu-id="f1abe-104">여 [Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="f1abe-104">by [Microsoft](https://github.com/microsoft)</span></span>

[<span data-ttu-id="f1abe-105">코드 다운로드</span><span class="sxs-lookup"><span data-stu-id="f1abe-105">Download Code</span></span>](iteration-2-make-the-application-look-nice-cs/_static/contactmanager_2_cs1.zip)

> <span data-ttu-id="f1abe-106">이 반복에서 기본 ASP.NET MVC 뷰 마스터 페이지를 수정 및 스타일 시트를 연계 하 여 응용 프로그램의 모양을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-106">In this iteration, we improve the appearance of the application by modifying the default ASP.NET MVC view master page and cascading style sheet.</span></span>


## <a name="building-a-contact-management-aspnet-mvc-application-c"></a><span data-ttu-id="f1abe-107">ASP.NET MVC 연락처 관리 응용 프로그램 (C#) 빌드</span><span class="sxs-lookup"><span data-stu-id="f1abe-107">Building a Contact Management ASP.NET MVC Application (C#)</span></span>
  

<span data-ttu-id="f1abe-108">이 일련의 자습서에서는 전체 연락처 관리 응용을 프로그램의 시작 끝나기를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-108">In this series of tutorials, we build an entire Contact Management application from start to finish.</span></span> <span data-ttu-id="f1abe-109">관리자에 게 문의 응용 프로그램을 사람 목록에 대 한 사용-이름, 전화 번호 및 전자 메일 주소-연락처 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-109">The Contact Manager application enables you to store contact information - names, phone numbers and email addresses - for a list of people.</span></span>

<span data-ttu-id="f1abe-110">여러 반복을 통해에 응용 프로그램을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-110">We build the application over multiple iterations.</span></span> <span data-ttu-id="f1abe-111">각 반복에서 점진적으로 응용 프로그램을 개선 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-111">With each iteration, we gradually improve the application.</span></span> <span data-ttu-id="f1abe-112">이 여러 개의 반복 접근 방법의 목적은 각 변경의 이유를 이해 하는 데 사용할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-112">The goal of this multiple iteration approach is to enable you to understand the reason for each change.</span></span>

- <span data-ttu-id="f1abe-113">반복 #1-응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-113">Iteration #1 - Create the application.</span></span> <span data-ttu-id="f1abe-114">첫 번째 반복에서는 만듭니다 연락처 관리자에는 가장 간단한 방법은 가능한.</span><span class="sxs-lookup"><span data-stu-id="f1abe-114">In the first iteration, we create the Contact Manager in the simplest way possible.</span></span> <span data-ttu-id="f1abe-115">기본적인 데이터베이스 작업에 대 한 지원을 추가 하 여: 만들기, 읽기, 업데이트 및 삭제 (CRUD).</span><span class="sxs-lookup"><span data-stu-id="f1abe-115">We add support for basic database operations: Create, Read, Update, and Delete (CRUD).</span></span>

- <span data-ttu-id="f1abe-116">반복 #2-모양이 아닌 응용 프로그램을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-116">Iteration #2 - Make the application look nice.</span></span> <span data-ttu-id="f1abe-117">이 반복에서 기본 ASP.NET MVC 뷰 마스터 페이지를 수정 및 스타일 시트를 연계 하 여 응용 프로그램의 모양을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-117">In this iteration, we improve the appearance of the application by modifying the default ASP.NET MVC view master page and cascading style sheet.</span></span>

- <span data-ttu-id="f1abe-118">반복 #3-폼 유효성 검사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-118">Iteration #3 - Add form validation.</span></span> <span data-ttu-id="f1abe-119">세 번째 반복에서 기본적인 형태의 유효성 검사를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-119">In the third iteration, we add basic form validation.</span></span> <span data-ttu-id="f1abe-120">म 중이거나 사용자에서 필수 양식 필드를 완료 하지 않고 폼을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-120">We prevent people from submitting a form without completing required form fields.</span></span> <span data-ttu-id="f1abe-121">또한 전자 메일 주소, 전화 번호를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-121">We also validate email addresses and phone numbers.</span></span>

- <span data-ttu-id="f1abe-122">반복 #4-느슨하게 결합 된 응용 프로그램을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-122">Iteration #4 - Make the application loosely coupled.</span></span> <span data-ttu-id="f1abe-123">이 세 번째 반복에서 우리 활용 여러 가지 소프트웨어 디자인 패턴을 쉽게 유지 관리 하 고 않아 응용 프로그램을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-123">In this third iteration, we take advantage of several software design patterns to make it easier to maintain and modify the Contact Manager application.</span></span> <span data-ttu-id="f1abe-124">예를 들어 리팩터링한 리포지토리 패턴 및 종속성 주입 패턴을 사용 하도록 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-124">For example, we refactor our application to use the Repository pattern and the Dependency Injection pattern.</span></span>

- <span data-ttu-id="f1abe-125">반복 #5-단위 테스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-125">Iteration #5 - Create unit tests.</span></span> <span data-ttu-id="f1abe-126">다섯 번째 반복에서 하도록 응용 프로그램이 쉽게 유지 관리 및 단위 테스트를 추가 하 여 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-126">In the fifth iteration, we make our application easier to maintain and modify by adding unit tests.</span></span> <span data-ttu-id="f1abe-127">데이터 모델 클래스를 모의 하 고 우리의 컨트롤러 및 유효성 검사 논리에 대 한 단위 테스트를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-127">We mock our data model classes and build unit tests for our controllers and validation logic.</span></span>

- <span data-ttu-id="f1abe-128">반복 6-테스트 기반 개발을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-128">Iteration #6 - Use test-driven development.</span></span> <span data-ttu-id="f1abe-129">이 6 번째 반복에서에서는 새 기능을 추가할 응용 프로그램 먼저 단위 테스트를 작성 하 고 단위 테스트에 대해 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-129">In this sixth iteration, we add new functionality to our application by writing unit tests first and writing code against the unit tests.</span></span> <span data-ttu-id="f1abe-130">이 반복 메일 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-130">In this iteration, we add contact groups.</span></span>

- <span data-ttu-id="f1abe-131">반복 #7-Ajax 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-131">Iteration #7 - Add Ajax functionality.</span></span> <span data-ttu-id="f1abe-132">일곱 번째 반복에서 개선할 응용 프로그램의 성능과 응답성 ajax 지원을 추가 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-132">In the seventh iteration, we improve the responsiveness and performance of our application by adding support for Ajax.</span></span>

## <a name="this-iteration"></a><span data-ttu-id="f1abe-133">이 반복</span><span class="sxs-lookup"><span data-stu-id="f1abe-133">This Iteration</span></span>

<span data-ttu-id="f1abe-134">이 반복의 목표 않아 응용 프로그램의 모양을 개선 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-134">The goal of this iteration is to improve the appearance of the Contact Manager application.</span></span> <span data-ttu-id="f1abe-135">현재, 연락처 관리자는 기본 ASP.NET MVC 뷰 마스터 페이지 및 연계 스타일 시트 (그림 1 참조)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-135">Currently, the Contact Manager uses the default ASP.NET MVC view master page and cascading style sheet (see Figure 1).</span></span> <span data-ttu-id="f1abe-136">이러한 안 불량, 보이지만 원하지 동일 하 게 다른 모든 ASP.NET MVC 웹 사이트를 않아 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-136">These don t look bad, but I don t want the Contact Manager to look just like every other ASP.NET MVC website.</span></span> <span data-ttu-id="f1abe-137">사용자 지정 파일에 이러한 파일을 대체 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-137">I want to replace these files with custom files.</span></span>


<span data-ttu-id="f1abe-138">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image1.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-138">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image1.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image1.png)</span></span>

<span data-ttu-id="f1abe-139">**그림 01**: ASP.NET MVC 응용 프로그램의 기본 모양을 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image2.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-139">**Figure 01**: The default appearance of an ASP.NET MVC Application ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image2.png))</span></span>


<span data-ttu-id="f1abe-140">이 반복 응용 프로그램의 시각적 디자인을 개선 하는 데 두 가지 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-140">In this iteration, I discuss two approaches to improving the visual design of our application.</span></span> <span data-ttu-id="f1abe-141">첫째, 방법을 보여 무료 ASP.NET MVC 디자인 서식 파일을 다운로드 하려면 ASP.NET MVC 디자인 갤러리를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-141">First, I show you how to take advantage of the ASP.NET MVC Design gallery to download a free ASP.NET MVC design template.</span></span> <span data-ttu-id="f1abe-142">ASP.NET MVC 디자인 갤러리를 사용 하는 작업을 수행 하지 않고 전문 웹 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-142">The ASP.NET MVC Design gallery enables you to create a professional web application without doing any work.</span></span>

<span data-ttu-id="f1abe-143">않아 응용 프로그램에 대 한 ASP.NET MVC 디자인 갤러리에서 서식 파일을 사용 하지 않도록 하기로 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-143">I decided to not use a template from the ASP.NET MVC Design gallery for the Contact Manager application.</span></span> <span data-ttu-id="f1abe-144">대신, 전문 디자인 회사에서 만든 사용자 지정 디자인을 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-144">Instead, I had a custom design created by a professional design firm.</span></span> <span data-ttu-id="f1abe-145">이 자습서의 두 번째 부분에서 최종 ASP.NET MVC 디자인을 만드는 전문가 디자인 회사와 저는 각 I 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-145">In the second part of this tutorial, I explain how I worked with a professional design company to create the final ASP.NET MVC design.</span></span>

## <a name="the-aspnet-mvc-design-gallery"></a><span data-ttu-id="f1abe-146">ASP.NET MVC 디자인 갤러리</span><span class="sxs-lookup"><span data-stu-id="f1abe-146">The ASP.NET MVC Design Gallery</span></span>

<span data-ttu-id="f1abe-147">ASP.NET MVC 디자인 갤러리에는 Microsoft에서 제공 무료 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-147">The ASP.NET MVC Design Gallery is a free resource provided by Microsoft.</span></span> <span data-ttu-id="f1abe-148">ASP.NET MVC 갤러리는 다음 주소에:</span><span class="sxs-lookup"><span data-stu-id="f1abe-148">The ASP.NET MVC Gallery is located at the following address:</span></span>

[<span data-ttu-id="f1abe-149">https://www.asp.net/mvc/gallery</span><span class="sxs-lookup"><span data-stu-id="f1abe-149">https://www.asp.net/mvc/gallery</span></span>](https://www.asp.net/mvc/gallery)

<span data-ttu-id="f1abe-150">ASP.NET MVC 디자인 갤러리 ASP.NET MVC 프로젝트에 사용 하기 위해 생성 된 무료 웹 사이트 디자인의 컬렉션을 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-150">The ASP.NET MVC Design Gallery hosts a collection of free website designs that were created specifically for using in an ASP.NET MVC project.</span></span> <span data-ttu-id="f1abe-151">설계는 커뮤니티의 회원이 업로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-151">Designs are uploaded by members of the community.</span></span> <span data-ttu-id="f1abe-152">갤러리 방문자가 즐겨 찾는 설계에 대 한 투표 수 있습니다 (그림 2 참조).</span><span class="sxs-lookup"><span data-stu-id="f1abe-152">Visitors to the Gallery can vote for their favorite designs (see Figure 2).</span></span>


<span data-ttu-id="f1abe-153">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image2.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image3.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-153">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image2.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image3.png)</span></span>

<span data-ttu-id="f1abe-154">**그림 02**: The ASP.NET MVC 디자인 갤러리 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image4.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-154">**Figure 02**: The ASP.NET MVC Design Gallery ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image4.png))</span></span>


<span data-ttu-id="f1abe-155">이 자습서를 쓰고 갤러리에서 가장 인기 있는 디자인 David Hauser 여 년 10 월 이라는 노드 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-155">As I write this tutorial, the most popular design in the gallery is a design named October by David Hauser.</span></span> <span data-ttu-id="f1abe-156">다음 단계를 완료 하 여 ASP.NET MVC 프로젝트에 대 한이 디자인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-156">You can use this design for an ASP.NET MVC project by completing the following steps:</span></span>

1. <span data-ttu-id="f1abe-157">클릭는 **다운로드** 단추를 사용자 컴퓨터로 October.zip 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-157">Click the **Download** button to download the October.zip file to your computer.</span></span>
2. <span data-ttu-id="f1abe-158">다운로드 한 October.zip 파일을 마우스 오른쪽 단추로 클릭 하 고 클릭는 **차단 해제** 단추 (그림 3 참조).</span><span class="sxs-lookup"><span data-stu-id="f1abe-158">Right-click the downloaded October.zip file and click the **Unblock** button (see Figure 3).</span></span>
3. <span data-ttu-id="f1abe-159">10 월 이라는 폴더에 파일을 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-159">Unzip the file to a folder named October.</span></span>
4. <span data-ttu-id="f1abe-160">10 월 폴더에 포함 된 DesignTemplate 폴더에서 모든 파일을 선택 합니다. 해당 파일을 마우스 오른쪽 단추로 클릭 하 고 메뉴 옵션을 선택 **복사**합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-160">Select all of the files from the DesignTemplate folder contained in the October folder, right-click the files, and select the menu option **Copy**.</span></span>
5. <span data-ttu-id="f1abe-161">Visual Studio 솔루션 탐색기 창에서 ContactManager 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 메뉴 옵션을 선택 **붙여넣기** (그림 4 참조).</span><span class="sxs-lookup"><span data-stu-id="f1abe-161">Right-click the ContactManager project node in the Visual Studio Solution Explorer window and select the menu option **Paste** (see Figure 4).</span></span>
6. <span data-ttu-id="f1abe-162">Visual Studio 메뉴 옵션을 선택 **편집, 찾기 및 바꾸기, 빠른 바꾸기** 바꾸고 *[MyProjectName]* 와 *ContactManager* (그림 5 참조).</span><span class="sxs-lookup"><span data-stu-id="f1abe-162">Select the Visual Studio menu option **Edit, Find and Replace, Quick Replace** and replace *[MyProjectName]* with *ContactManager* (see Figure 5).</span></span>


<span data-ttu-id="f1abe-163">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image3.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image5.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-163">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image3.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image5.png)</span></span>

<span data-ttu-id="f1abe-164">**그림 03**:는 웹에서 다운로드 한 파일을 차단 해제 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-164">**Figure 03**: Unblocking a file downloaded from the web ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image6.png))</span></span>


<span data-ttu-id="f1abe-165">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image4.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-165">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image4.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image7.png)</span></span>

<span data-ttu-id="f1abe-166">**그림 04**: 솔루션 탐색기에서 파일을 덮어쓰지 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image8.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-166">**Figure 04**: Overwriting files in the Solution Explorer ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image8.png))</span></span>


<span data-ttu-id="f1abe-167">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image5.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image9.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-167">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image5.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image9.png)</span></span>

<span data-ttu-id="f1abe-168">**그림 05**: ContactManager [이름] 경로로 바꿉니다 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image10.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-168">**Figure 05**: Replacing [ProjectName] with ContactManager ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image10.png))</span></span>


<span data-ttu-id="f1abe-169">다음이 단계를 완료 한 후 웹 응용 프로그램의 새로운 디자인을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-169">After you complete these steps, your web application will use the new design.</span></span> <span data-ttu-id="f1abe-170">그림 6에 있는 페이지와 년 10 월 디자인 않아 응용 프로그램의 모양을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-170">The page in Figure 6 illustrates the appearance of the Contact Manager application with the October design.</span></span>


<span data-ttu-id="f1abe-171">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image6.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image11.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-171">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image6.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image11.png)</span></span>

<span data-ttu-id="f1abe-172">**그림 06**: ContactManager 년 10 월 템플릿으로 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image12.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-172">**Figure 06**: ContactManager with the October template ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image12.png))</span></span>


## <a name="creating-a-custom-aspnet-mvc-design"></a><span data-ttu-id="f1abe-173">사용자 지정 ASP.NET MVC 디자인 만들기</span><span class="sxs-lookup"><span data-stu-id="f1abe-173">Creating a Custom ASP.NET MVC Design</span></span>

<span data-ttu-id="f1abe-174">ASP.NET MVC 디자인 갤러리 좋은 선택한 다른 디자인 스타일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-174">The ASP.NET MVC Design Gallery has a good selection of different design styles.</span></span> <span data-ttu-id="f1abe-175">갤러리는 ASP.NET MVC 응용 프로그램의 모양을 사용자 지정할 수 있는 간편한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-175">The Gallery provides you with a painless way to customize the appearance of your ASP.NET MVC applications.</span></span> <span data-ttu-id="f1abe-176">및 물론, 갤러리가 완전히 들지 큰 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-176">And, of course, the Gallery has the big advantage of being completely free.</span></span>

<span data-ttu-id="f1abe-177">그러나 웹 사이트에 대 한 완전히 고유한 디자인을 만드는 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-177">However, you might need to create a completely unique design for your website.</span></span> <span data-ttu-id="f1abe-178">이 경우에 웹 사이트 디자인 회사에서 실행 되도록 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-178">In that case, it makes sense to work with a website design company.</span></span> <span data-ttu-id="f1abe-179">이 접근 방식을 않아 응용 프로그램에 대 한 디자인에 대 한 하기로 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-179">I decided to take this approach for the design for the Contact Manager application.</span></span>

<span data-ttu-id="f1abe-180">반복 # 1에서 연락처 관리자를 압축 하 고 설계 회사에 프로젝트를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-180">I zipped up the Contact Manager from Iteration #1 and sent the project to the design company.</span></span> <span data-ttu-id="f1abe-181">해당 않았음에도 t 문제를 나타내지 (참에!), Visual Studio를 소유 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-181">They did not own Visual Studio (shame on them!), but that didn t present a problem.</span></span> <span data-ttu-id="f1abe-182">Microsoft Visual Web Developer를 무료로 다운로드할 수 있었던는 [https://www.asp.net](https://www.asp.net) 웹 사이트 및 Visual Web Developer에서 않아 응용 프로그램을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-182">They were able to download Microsoft Visual Web Developer for free from the [https://www.asp.net](https://www.asp.net) website and open the Contact Manager application in Visual Web Developer.</span></span> <span data-ttu-id="f1abe-183">며칠, 그림 7에 디자인 얻은 결과 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-183">In a couple of days, they had produced the design in Figure 7.</span></span>


<span data-ttu-id="f1abe-184">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image7.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image13.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-184">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image7.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image13.png)</span></span>

<span data-ttu-id="f1abe-185">**그림 07**: ASP.NET MVC 않아 디자인 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image14.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-185">**Figure 07**: The ASP.NET MVC Contact Manager Design ([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image14.png))</span></span>


<span data-ttu-id="f1abe-186">두 가지 주요 파일 하는 구성 된 새로운 디자인: 새 연계 스타일 시트 파일 및 새 뷰 마스터 페이지 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-186">The new design consisted of two main files: a new cascading style sheet file and a new view master page file.</span></span> <span data-ttu-id="f1abe-187">뷰 마스터 페이지 레이아웃 및 ASP.NET MVC 응용 프로그램의 뷰에 대 한 공유 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-187">A view master page contains the layout and shared content for views in an ASP.NET MVC application.</span></span> <span data-ttu-id="f1abe-188">예를 들어 뷰 마스터 페이지 그림 7에서는 머리글, 탐색 탭 및 표시 되는 바닥글을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-188">For example, the view master page includes the header, navigation tabs, and footer that appear in Figure 7.</span></span> <span data-ttu-id="f1abe-189">설계 회사에서 새 Site.Master 파일 Views\Shared 폴더에서에서 기존 Site.Master 뷰 마스터 페이지를 덮어쓴 I</span><span class="sxs-lookup"><span data-stu-id="f1abe-189">I overwrote the existing Site.Master view master page in the Views\Shared folder with the new Site.Master file from the design company,</span></span>

<span data-ttu-id="f1abe-190">설계 회사 연계 새 스타일 시트 및 이미지의 집합에도 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-190">The design company also created a new cascading style sheet and set of images.</span></span> <span data-ttu-id="f1abe-191">이러한 새 파일의 콘텐츠 폴더에 배치 하 고 기존 Site.css 파일을 덮어썼습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-191">I placed these new files in the Content folder and overwrote the existing Site.css file.</span></span> <span data-ttu-id="f1abe-192">콘텐츠 폴더에 모든 정적 콘텐츠를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-192">You should place all static content in the Content folder.</span></span>

<span data-ttu-id="f1abe-193">Contact Manager에 대 한 새로운 디자인에 이미지를 편집 하 고 연락처 삭제를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-193">Notice that the new design for the Contact Manager includes images for editing and deleting contacts.</span></span> <span data-ttu-id="f1abe-194">연락처의 HTML 테이블에 각 연락처 옆으로 편집 및 삭제 이미지로가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-194">An Edit and Delete image appear next to each contact in the HTML table of contacts.</span></span>

<span data-ttu-id="f1abe-195">HTML 렌더링 된 다음 링크를 원래, 합니다. 다음과 같은 도우미 ActionLink():</span><span class="sxs-lookup"><span data-stu-id="f1abe-195">Originally, these links that were rendered with the HTML.ActionLink() helper like this:</span></span>

[!code-aspx[Main](iteration-2-make-the-application-look-nice-cs/samples/sample1.aspx)]

<span data-ttu-id="f1abe-196">Html.ActionLink() 메서드 (HTML 메서드 보안상의 이유로 대 한 링크 텍스트를 인코딩합니다) 이미지를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-196">The Html.ActionLink() method does not support images (the method HTML encodes the link text for security reasons).</span></span> <span data-ttu-id="f1abe-197">따라서 다음과 같이 Url.Action() 호출 하 여 Html.ActionLink()에 대 한 호출을 교체 I.</span><span class="sxs-lookup"><span data-stu-id="f1abe-197">Therefore, I replaced the calls to Html.ActionLink() with calls to Url.Action() like this:</span></span>

[!code-aspx[Main](iteration-2-make-the-application-look-nice-cs/samples/sample2.aspx)]

<span data-ttu-id="f1abe-198">Html.ActionLink() 메서드는 전체 HTML 하이퍼링크를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-198">The Html.ActionLink() method renders an entire HTML hyperlink.</span></span> <span data-ttu-id="f1abe-199">Url.Action() 메서드 반면에 렌더링 하는 URL만 하지 않고는 &lt;는&gt; 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-199">The Url.Action() method, on the other hand, renders just the URL without the &lt;a&gt; tag.</span></span>

<span data-ttu-id="f1abe-200">또한 새로운 디자인에 선택 및 선택 되지 않은 탭이 포함 되어 있는지 확인할 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-200">Notice, furthermore, that the new design includes both selected and unselected tabs.</span></span> <span data-ttu-id="f1abe-201">그림 8의 예를 들어는 **새 연락처 만들기** 탭을 선택 및 **내 연락처** 탭이 선택 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-201">For example, in Figure 8, the **Create New Contact** tab is selected and the **My Contacts** tab is not selected.</span></span>


<span data-ttu-id="f1abe-202">[![새 프로젝트 대화 상자](iteration-2-make-the-application-look-nice-cs/_static/image8.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image15.png)</span><span class="sxs-lookup"><span data-stu-id="f1abe-202">[![The New Project dialog box](iteration-2-make-the-application-look-nice-cs/_static/image8.jpg)](iteration-2-make-the-application-look-nice-cs/_static/image15.png)</span></span>

<span data-ttu-id="f1abe-203">**그림 08**: 선택한 탭을 선택 하지 않은 ([전체 크기 이미지를 보려면 클릭](iteration-2-make-the-application-look-nice-cs/_static/image16.png))</span><span class="sxs-lookup"><span data-stu-id="f1abe-203">**Figure 08**: Selected and unselected tabs([Click to view full-size image](iteration-2-make-the-application-look-nice-cs/_static/image16.png))</span></span>


<span data-ttu-id="f1abe-204">선택 및 선택 되지 않은 탭 렌더링를 지원 하기 위해 필자는 MenuItemHelper 라는 사용자 지정 HTML 도우미를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-204">To support rendering both selected and unselected tabs, I created a custom HTML helper named the MenuItemHelper.</span></span> <span data-ttu-id="f1abe-205">이 도우미 메서드를 렌더링 하거나는 &lt;li&gt; 태그 또는 &lt;li 클래스 "선택" =&gt; 현재 컨트롤러 및 작업 도우미에 전달 된 컨트롤러 및 작업 이름에 해당 하는 여부에 따라 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-205">This helper method renders either a &lt;li&gt; tag or a &lt;li class="selected"&gt; tag depending on whether the current controller and action corresponds to the controller and action name passed to the helper.</span></span> <span data-ttu-id="f1abe-206">MenuItemHelper에 대 한 코드 목록 1에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-206">The code for the MenuItemHelper is contained in Listing 1.</span></span>

<span data-ttu-id="f1abe-207">**1-Helpers\MenuItemHelper.cs 나열**</span><span class="sxs-lookup"><span data-stu-id="f1abe-207">**Listing 1 - Helpers\MenuItemHelper.cs**</span></span>

[!code-csharp[Main](iteration-2-make-the-application-look-nice-cs/samples/sample3.cs)]

<span data-ttu-id="f1abe-208">MenuItemHelper를 사용 하 여 TagBuilder 클래스 내부적으로 작성 된 &lt;li&gt; HTML 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-208">The MenuItemHelper uses the TagBuilder class internally to build the &lt;li&gt; HTML tag.</span></span> <span data-ttu-id="f1abe-209">TagBuilder 클래스는 새 HTML 태그를 작성 해야 할 때마다 사용할 수 있는 매우 유용한 유틸리티 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-209">The TagBuilder class is a very useful utility class that you can use whenever you need to build up a new HTML tag.</span></span> <span data-ttu-id="f1abe-210">특성을 추가, CSS 클래스를 추가 하 고, Id, 생성 하 고 s 태그를 수정 하기 위한 메서드 포함 내부 HTML입니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-210">It includes methods for adding attributes, adding CSS classes, generating Ids, and modifying the tag s inner HTML.</span></span>

## <a name="summary"></a><span data-ttu-id="f1abe-211">요약</span><span class="sxs-lookup"><span data-stu-id="f1abe-211">Summary</span></span>

<span data-ttu-id="f1abe-212">이 반복에 ASP.NET MVC 응용 프로그램의 시각적 디자인을 개선 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-212">In this iteration, we improved the visual design of our ASP.NET MVC application.</span></span> <span data-ttu-id="f1abe-213">첫째, ASP.NET MVC 디자인 갤러리에 도입 된 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-213">First, you were introduced to the ASP.NET MVC Design Gallery.</span></span> <span data-ttu-id="f1abe-214">ASP.NET MVC 응용 프로그램에서 사용할 수 있는 ASP.NET MVC 디자인 갤러리에서 무료 디자인 서식 파일을 다운로드 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-214">You learned how to download free design templates from the ASP.NET MVC Design Gallery that you can use in your ASP.NET MVC applications.</span></span>

<span data-ttu-id="f1abe-215">다음으로, 기본 연계 스타일 시트 파일 및 마스터 뷰 페이지 파일을 수정 하 여 사용자 지정 디자인을 만들 수는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-215">Next, we discussed how you can create a custom design by modifying the default cascading style sheet file and master view page file.</span></span> <span data-ttu-id="f1abe-216">새 디자인을 지원 하기 위해 몇 가지 사소한 변경 않아 응용 프로그램을 만들어야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-216">In order to support the new design, we had to make some minor changes to our Contact Manager application.</span></span> <span data-ttu-id="f1abe-217">예를 들어 라는 MenuItemHelper 또는 선택 하지 않은 탭이 표시 되는 새 HTML 도우미를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-217">For example, we added a new HTML helper named the MenuItemHelper that displays selected and unselected tabs.</span></span>

<span data-ttu-id="f1abe-218">다음 반복에서 유효성 검사의 매우 중요 한 주제를 해결할 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-218">In the next iteration, we tackle the very important subject of validation.</span></span> <span data-ttu-id="f1abe-219">사용자 먼저 사용자 s 등 필요한 값을 제공 하지 않고 새 연락처를 만들 수 없습니다 및 성을 유효성 검사 코드에 응용 프로그램을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1abe-219">We add validation code to our application so that a user cannot create a new contact without supplying required values such as a person s first and last name.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f1abe-220">[이전](iteration-1-create-the-application-cs.md)
[다음](iteration-3-add-form-validation-cs.md)</span><span class="sxs-lookup"><span data-stu-id="f1abe-220">[Previous](iteration-1-create-the-application-cs.md)
[Next](iteration-3-add-form-validation-cs.md)</span></span>