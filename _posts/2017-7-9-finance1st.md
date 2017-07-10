---
layout: post
title: finance 환경 구축하기
---
1. dart crawling

-Dart API에서 리스트를가져온다 다음과 같은 형태
  1) http://dart.fss.or.kr/dsaf001/main.do?rcpNo=접수번호
-해당 접수번호를 알게 되면 해당 페이지 크롤링이 가능하며 이때 아래 형태를 크롤링한다
  1)<a href="#download" onclick="openPdfDownload('20150326000802', '4533550'); return false;"><img src="/images/common/viewer_down.gif" style="cursor:pointer;" alt="다운로드" title="다운로드"></a>
  2) 4533550이 PDF 번호임
 -PDF의 최종 주소는 다음과 같다. 이를 wget으로 가져와서 python에서 PDF 처리 한다.
  1) https://dart.fss.or.kr/pdf/download/pdf.do?rcp_no=20150326000802&dcm_no=4533550
   
혹은 아래와 같이 할 수 있지만, 상기의 방법이 더 이상적임

2. https://financedata.github.io/posts/naver-finance-finstate-crawling.html

3. https://woosa7.github.io/fss_dart/
